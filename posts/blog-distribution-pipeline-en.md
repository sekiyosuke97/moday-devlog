<!-- canonical: https://moday.me/blogs/journal/blog-distribution-pipeline -->

# One Post, Nine Languages, Ten Platforms: The MODAY Distribution Pipeline

## Write once in Japanese, land in nine languages across ten places

Here's what happens when I finish writing one Japanese draft for the MODAY devlog:

| Tier | Destination |
|---|---|
| Owned | Shopify Blog (JA + 8 locales) |
| Auto-distributed via API | dev.to / Qiita / Zenn / GitHub devlog |
| Manual paste, handoff files generated | note / Medium / Tumblr |

The whole job on the writing side is: finish the draft, run `distribute.py` once. The rest spreads on its own.

I built this pipeline in three days and have been running every post through it since post #1. Here's the actual shape of the thing.

## The design call: split "auto" and "manual" from the start

The first thing I decided was to **separate the targets into two tiers**.

Platforms with a working write API (Shopify, dev.to, Qiita, Zenn-via-GitHub, GitHub itself) on one side. Platforms with no API or a hostile one (note, Medium, Tumblr) on the other. The moment you try to unify these, the script turns into a swamp.

So:

- Auto tier — `distribute.py` does everything over HTTP
- Manual tier — `prepare_handoff.py` emits **paste-ready files** that a human carries to the UI

The manual tier is the part I haven't been able to hand to AI yet. But everything up to the moment of pasting is automated.

## What `distribute.py` actually does

The flow inside `distribute.py`:

1. **Hero gate at startup**. If `content/posts/<slug>/hero.png` is missing, the script halts. No cover image, no distribution. It's a structural guard against "oops I forgot the hero."
2. **Post to the Shopify Journal blog**, body + hero in one shot.
3. **Register Shopify translations**. Reads sibling files `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` and stuffs all eight locales in via the `translationsRegister` API in one batch.
4. **POST to dev.to**, EN body, with the Shopify CDN URL reused as the cover.
5. **POST to Qiita**, JA body with `canonical_url` pointing back to Shopify.
6. **Zenn — no API call**. Zenn doesn't expose a write API, so I configured the Zenn ↔ GitHub sync. A push lands a post automatically.
7. **GitHub devlog**: commits `<slug>-ja.md`, `<slug>-en.md`, `<slug>-hero.png` to the `moday-devlog` repo.
8. **Calls `prepare_handoff.py`** to generate the manual-tier paste files.
9. **Writes `status.json`** alongside the source, recording URL/ID/timestamp for every platform.

The two parts I'm most pleased with are the **hero gate** and the **Zenn-via-GitHub route**. The hero gate makes it structurally impossible to ship a post without a cover image. And Zenn — which deliberately doesn't expose write APIs — still gets the post, because a `git push` is all the bridge needs.

## What `prepare_handoff.py` does

Produces paste-ready files for the three manual destinations:

| File | Contents | Language |
|---|---|---|
| `note.md` | JA original with paste-instruction comments. Tables get converted to "**Label:** value" paragraphs because note doesn't render Markdown tables. | JA |
| `medium.html` | EN translation as HTML. Instruction banner at the top with copy-disabled CSS, body underneath. ⌘+A → ⌘+C copies the body only. | EN |
| `tumblr.md` | EN lede (H1 through the first H2, hard-capped at 1500 chars) + canonical link + Tumblr-style tag block. | EN |

The non-obvious bit here is the **per-platform dialect**.

note doesn't render Markdown tables — paste the raw thing and you get `| header | value |` displayed as literal text, which looks terrible. So `prepare_handoff.py` rewrites every table into bold-label paragraphs.

Medium has the opposite problem: copy-paste from anywhere tends to drag metadata in. I wanted the writer (me) to be able to ⌘+A → ⌘+C the page and get *only the body*. So the output HTML has an instructions banner at the top with `user-select: none` CSS — visible to the writer, invisible to the clipboard.

Tumblr culture doesn't reward dumping a 3,000-word essay into a post. So I excerpt just the lede and link back to the canonical.

Each platform gets its **dialect and culture** respected, in one centralized place.

## I let AI do the translation too — but only inside the subscription

The whole MODAY pitch is "an AI-driven brand build," so of course the translation goes to AI too. I changed how, recently.

- Before: `distribute.py` called the Anthropic API with Claude Haiku for each locale.
- Now: I ask Claude Code (Opus 4.7) directly to "rewrite this for eight locales," in-session.

The reason is dumb and unsexy: **I don't want a second metered bill**. I already pay for Claude Max. Anything that can happen inside that subscription should happen inside that subscription.

This is less a technical call than a **business one**. For a one-person shop, the most important thing is keeping fixed costs down. Running a Claude Max subscription *and* a metered Anthropic API charge against the same task is a sloppy way to run a personal P&L.

The other thing that mattered: **quality**. The Haiku-via-API outputs read like translations — workable, but not native. Going to nine locales means I need rewrites that read as if a native founder wrote them locally. Without that, the brand doesn't land in any of those markets.

That kind of rewrite isn't translation; it's localization-rewrite. Running it through Claude Code on Opus 4.7 gave me noticeably better output than the previous Haiku-API pipeline.

Cutting the cost actually raised the quality. Wasn't expecting that.

## The actual day-to-day

The operational rhythm now looks like:

1. Draft a JA post in mobile Claude (usually on a train).
2. In a Claude Code session, drop it at `webhook/posts/004-<slug>-ja.md`.
3. Ask Claude Code to "rewrite for eight locales" — it produces `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`.
4. Generate the hero with `webhook/generate_hero.py` → `content/posts/<slug>/hero.png`.
5. Run `python webhook/distribute.py webhook/posts/004-<slug>-ja.md`.
   - Auto-distributes to Shopify (JA + 8 locales), dev.to, Qiita, GitHub.
   - Calls `prepare_handoff.py` to drop `content/posts/<slug>/{note.md, medium.html, tumblr.md}`.
6. Open note / Medium / Tumblr in a browser, paste the prepared files.

The only step where I actually *think* is step 1. The rest is instructions to Claude Code, a script run, and pasting.

## From "had an idea on the train" to "everything's live" in one day

The part of this I like most isn't even the script — it's the **human-side flow**.

Ideas hit me when I'm away from a desk. Commuting. Right before sleep. Walking somewhere. That's when I open mobile Claude, pull up the MODAY project, and talk through the post. By the time I'm home, the draft is basically done.

At the desk, I open Claude Code, hand it the draft, it produces the locale rewrites and runs the pipeline.

The amount of time I spend *sitting at a desk pushing words around* is close to zero. That's the part of "AI-driven brand build" that actually feels real right now.

## Wrapping up

The pipeline itself was also written by Claude Code. I just said "I want a script that distributes to nine languages and ten platforms," and we worked the spec out in conversation.

Still on the to-do list: Tumblr API integration, a dashboard view of `status.json`, automated fan-out to social. I'll fold those in as the brand keeps moving.

More soon.

— Yoskee  
[moday.me](https://moday.me)

---

<!-- moday-product-card -->
### Wear the day. — Get the MODAY Tees

| Set | Pieces | Price |
|---|---|---|
| **[The Full Week →](https://moday.me/collections/bundle-full-week)** | Mon–Sun (7) | $159 |
| **[The Workweek →](https://moday.me/collections/bundle-workweek)** | Mon–Fri (5) | $119 |
| **[Starter Pack →](https://moday.me/collections/bundle-starter)** | Mon · Wed · Fri (3) | $79 |
| **[The Weekend →](https://moday.me/collections/bundle-weekend)** | Sat · Sun (2) | $55 |

*Free shipping over $99 · 8 colors × 6 sizes · 9 languages*
