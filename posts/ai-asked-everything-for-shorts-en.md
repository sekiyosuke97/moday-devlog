<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# To make short-form videos, I asked AI every single thing I didn't know

## Retracting what I said about "the observation loop"

In an earlier post I wrote that "the observation loop started" — that the moment we opened, the world began talking back.

Four or five days in, here's what I actually figured out: **the sample size is too small to observe anything.**

I can stare at GA4, follow cart behavior, scrape the chatbot logs — but the volume is so low that none of it produces a hypothesis worth acting on. To even start theorizing, more people have to walk in.

So the right move isn't observation yet. It's **getting the traffic up first.** I had the order wrong.

## Time to actually get hands dirty on acquisition

The whole build phase was about **constructing the machine**. Nine-language ten-platform distribution, an automated chatbot, automated order→production, an automated improvement loop. Everything filed under "build the system, then let it run."

I wanted acquisition to work the same way — ad budget pours in, data accumulates, AI proposes improvements, automate the loop, done.

But there's no ad budget right now (covered that in another post). With paid off the table, **organic social is the only lane left**. Short-form video specifically — for a product this visual, the format should fit.

Except for one detail: **I have absolutely no idea what works on short-form right now.**

I don't watch Japanese shorts in any sustained way. English-language shorts? Even less. I do e-commerce consulting for a living, and this is a weakness I just have to admit. I'm stepping into territory that isn't a strength.

## Step one: ask Gemini

I'd been watching the Google I/O news and wanted an excuse to put Gemini through its paces. So I asked: "What's trending in short-form video aimed at English-speaking business professionals on TikTok, LinkedIn, and Shorts?"

What came back was a world I knew nothing about:

- **Corporate buzzword satire** — sketches mocking the empty vocabulary of corporate speak: "Synergy," "Circle back," "Let's take this offline."
- **Self-aware "Day in the Life"** — riffs like "How to keep Teams 'Active' without getting out of bed," laughing at the cog-in-the-machine feeling.
- **Corporate Erin–type characters** — actors playing the cold HR persona, professional smile and rapid speech wrapping a layoff in cheerful cadence.
- **LinkedIn Lunatics** — TikTokers reading aloud and mocking the poetry-fied business posts people seriously publish on LinkedIn.

The pattern Gemini pulled out hit hard. The throughline of English-speaking business-humor virality is **"comedic mutiny against absurd corporate culture."**

That's adjacent territory to MODAY by definition. The world-view of a "MONDAY: System Booting…" tee and a "FRIDAY: Build Successful ✓" tee lives inside that same culture.

There is no way I would've landed on those four genres working from my own head.

## Step two: feed it to Codex and ask for a storyboard

I handed the Gemini output straight to Codex. Prompt: "Write the storyboard for a MODAY short-form acquisition video. 9:16 vertical, 22 seconds, English-speaking business audience, satire-and-humor tone, end on the brand."

What came back:

![Storyboard: Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

**"Weekdays Ranked by Developer Damage."** Concept: rank the days of the week by how much damage they inflict on a developer. Not a product showcase — a **meme that stands on its own**. Designed so the comment section starts arguing about the ranking, capped with "Tell me I'm wrong" as bait. Only at the end does the brand land: "MODAY — Wear the day you survived."

The product pitch is **hidden in the final two seconds**. The video doesn't read as an ad. It gets consumed as a meme. The comments do the lifting. Acquisition strategy is squarely inside my day-job's wheelhouse as a consultant — and this time I outsourced it completely to AI.

And the result is meaningfully better than what I would've drafted.

## Step three: spin up four reusable models in ChatGPT Image

A video series needs **characters you can reuse**. I can't afford to hire real people, and I don't have the time to shoot. ChatGPT Image 2.0 generated four models for me in one batch.

![Model 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Model 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Model 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Model 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

Ethnicity, age, and gender spread across the four. Each keeps a coherent vibe — engineer-ish, remote-worker-ish, office-professional-ish — but every model has its own face.

Each one came with front, three-quarter, and side angles plus several expressions, all from a single prompt. These are the recurring cast for the video series. **Four house models, exclusive to the brand.**

Renting a studio. Calling an agency. Sourcing wardrobe. Setting up lighting. All of it skipped. Cost is essentially zero. Total time, maybe thirty minutes.

## From here, I'm working by hand

The remaining steps:

1. Composite each scene as a still (model + the tee + background).
2. Animate the still into video.
3. Add SFX and captions.
4. Post to TikTok / Instagram Reels / YouTube Shorts.

For this round I'm pushing **multi-language fan-out and automation to the next step**. One English video first, made by hand, sent into the wild. If it hits, I scale the winning pattern to all nine languages and build the automation pipeline behind it. If it doesn't, I try a different angle.

This is straight out of the web-dev playbook: **build one working prototype by hand, only invest in automation once you can see the winning shape.** Acquisition follows the same rule.

## AI-driven, but I still step back to my own hands

I wrote in an earlier post: "hand off everything I can to AI." That policy hasn't changed. This round, the storyboard, the models, and the strategy were all AI-built.

But **the compositing and the editing of the first video, I'm doing by hand.** Not because AI couldn't technically do it. Because **I want the texture of the first one in my own hands.**

What catches. Where viewers drop off. What the comment section does. I can't develop the judgment for the automation phase unless I personally watch it happen. Build it by hand. Hit, miss, log the experience — that's **the raw material for the criteria** I'll need later.

The brand is AI-driven, but **the judgment stays mine.** When to delegate, when not to — that boundary is the founder's job. And right now is one of the "do it by hand" moments.

For the curious, here's the first video:

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

Whether the first one lands or flops, I don't know yet. Hit → automation. Miss → different angle. Either way, a new loop starts from here.

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
