<!-- canonical: https://moday.me/blogs/journal/15min-chatbot-render-comeback -->

# A 15-Minute Chatbot — I Ditched Render, Then Brought It Back

## From the missed opportunity on 5/19 to a live bot in 15 minutes

I wrote about this in another post: on 5/19, the first two customer inquiries came in. I couldn't reply same-day; my response went out the next morning.

I logged that as **lost opportunity**, and that same day I built a chatbot.

The usual little widget that sits in the bottom-right corner of the store. From "start working" to "deployed and live on Shopify," about 15 minutes. Here's what I know about what's actually inside it.

## The setup

Roughly, it looks like this.

- **Front end**: a bottom-right widget in the Shopify theme (I have no idea how it was implemented)
- **Backend**: Render.com hitting the Claude API
- **Languages**: tied to the Shopify locale, 9 languages
- **History**: written to a Google Sheet
- **Escalation**: questions it can't answer get routed to the contact form

The design philosophy is simple: **keep it simple**. That's the whole thing. At the solo-founder phase, whatever I'm building, I don't want to carry complexity.

## I ditched Render, then used it again

In another post I announced "**I'm done with FastAPI / Render**." Sounds like a contradiction, but what I dropped was the **webhook use case**. The flow that takes a Shopify order and pushes it into Gelato — that was running on FastAPI on Render. I swapped it out for a different architecture. (That migration is its own post; another time.)

The chatbot **brought Render back, in a different configuration.** The infra that used to host the webhook server, and the infra now hosting the chatbot API — same vendor, totally different roles, different services, different processes. The only thing they share is the word "Render."

"I ditched Render" and "I'm using Render" are not in conflict. **You pick the best tool for each job at the moment you make the call.** If you let past decisions lock you in — "I said I wouldn't use it, so I won't" — your judgment goes brittle.

I hold the judgment axis. Claude Code does the building. Every time we rebuild something, we go after the best answer available right now.

## Chat history goes into a Google Sheet

Every exchange between the bot and the user gets written to a Google Sheet. Timestamp, locale, the user's question, the bot's answer, whether it escalated.

This was Claude Code's suggestion, and I went with it. In hindsight it was the right call for three reasons.

1. **I don't want to run a database**: schema design, hosting cost, a separate viz layer. Too heavy for the solo phase.
2. **It's free**: a Google account is the only requirement, cost is zero.
3. **Easy to read later — for me and for Claude Code**: scan the columns and you've got the whole picture.

That third one is the big one. When I later ask Claude Code "**summarize recent inquiry patterns,**" it can read the sheet directly. With a database, I'd have to write an extraction script, dump to CSV, etc. Extra step.

A dedicated DB would be cleaner, but at this scale the sheet is plenty. At the solo-founder phase, this is **the right kind of lazy.**

## How the 9-language support works

Grab the current Shopify locale, hand it to the bot. The bot hits the Claude API with a prompt that says "**reply in this language**." No translation step in the middle. Claude writes directly in the target language.

In another post I wrote "not translation, but localization — a rewrite." Same principle applies to the bot. We don't write in Japanese and translate to English; from the first token, it's written in the voice of a native English speaker. German → native German. The whole thing happens inside the model, so both translation latency and mistranslation risk drop, structurally.

Nothing fancy here either. I just told Claude Code one line: "**take the Shopify locale and reply in that language.**"

## I told the prompt to "know the site"

The bot can answer anything that's on the MODAY site or in the Gelato product data. Shipping availability, lead times, sizes, payment methods, return policy, pricing, bundle composition.

I told Claude Code to "**know all of that.**"

To be honest: **I don't actually know how it knows.** Is it baked into the prompt? Is it fetching the site? Some combination? Claude Code decided and implemented.

Same pattern I wrote about elsewhere — I gave the directive, I delegated the implementation. It works, the answers come back correct, so for now that's enough. If it breaks, I'll tell Claude Code to fix it.

## Anything it can't answer goes to the contact form

Letting the bot answer everything is dangerous.

Size questions for specific bodies, gift wrapping, B2B inquiries, problem tickets. If the bot speaks with confidence on those, you create disputes later.

When the bot decides "I shouldn't answer this one," it pushes the user to the contact form. The guardrail design was also delegated to Claude Code. All I did was one line: "**send anything you can't answer to the contact form.**"

Which questions the bot fields, which ones it escalates — Claude Code drew that line. I figure I'll skim the logs occasionally and adjust if anything's clearly miscategorized, but so far, nothing.

The reason this shipped in 15 minutes is that there were very few decisions inside those 15 minutes.

"Bottom-right widget." "Claude API backend." "9 languages." "Bring Render back." "History to a sheet." "Escalation to the contact form." Once those are locked, Claude Code builds. I give the GO and check whether it works.

Day 2 of the store being open, the support automation foundation went live. The first "**one improvement per day**" was this one.

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
