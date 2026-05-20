<!-- canonical: https://moday.me/blogs/journal/how-i-use-claude-code -->

# How I Use Claude Code — Don't Organize, Delegate, Just Vibe

## Looking back, here's how I actually use Claude Code

I've been writing about building MODAY for weeks now, but I never wrote about **how I actually drive Claude Code**.

The stack I picked, the distribution pipeline I wired up, the nine-language localization, the chatbot I shipped in 15 minutes — all of that was the "**what I built**" side of the story.

The store is open. I'm in operations mode now. So it's time for the meta view.

The short version: **don't organize, delegate, just vibe.**

This is probably the opposite of most Claude Code advice you'll read online.

## Claude wrote my CLAUDE.md

The standard advice is: "**Write a clean CLAUDE.md with your project context.**" Brand info, stack, coding conventions, priorities. Lay it all out neatly so Claude Code can pick up the context. That's the textbook move.

In MODAY's CLAUDE.md, **I haven't written a single line myself.** I don't even fully know what's in it.

Early in the build, I told Claude Code, "feel free to maintain this file yourself." It started writing in brand info, the stack, the SKU table, Markets settings, phase-by-phase priorities. When I glance at it now and then, it's organized in a way that's *probably* more legible to Claude than anything I'd produce by hand.

Start to finish, I never did the "organizing" work. **I handed the act of organizing itself over to Claude.**

## I split sessions on vibes

I do split sessions. But **there's no rule.**

No strict by-purpose taxonomy. Loose buckets like "content," "UI/UX," "MD (misc stuff)." Image generation, translation, code — all of it gets mixed inside the same session.

I don't split by role like "translation session" vs "code session." **I split by the flow of the work.** It's sloppy, but it produces a state where one thought chains into the next.

I'll be tweaking the UI and suddenly think, "oh, the translations should change to match this." So I run the translations right there in the same session. The cost of dragging context across sessions is zero, so **the flow of judgment doesn't break.** That turns out to matter more than I expected.

## I barely give technical instructions

I wrote about this in another post: during stack selection, I didn't give a single technical condition. Everything I supplied was business-side. That stance hasn't changed once we got into implementation.

The one thing I actively communicate:

"**Use Shopify and Gelato the standard way. Keep custom implementation to a minimum.**"

I think this is the iron rule of SaaS. Staying inside the lane the vendor designed for is the most stable long-term play. Custom implementations are seductive in the short term and get destroyed by the next vendor update. Standard flows, standard APIs, standard theme structure. You only leave that lane when you absolutely have to.

Once that's clear, I can leave the API calls, the testing strategy, the error handling, the implementation details — pretty much all of it — to Claude Code.

## When it asks me, I tell it to figure it out itself

Claude Code asks for confirmation sometimes. "Can you show me the contents of this file?" "Is this okay?" "How should I write the tests?"

To almost all of it, my answer is: "**figure it out yourself.**"

If it wants to see a file, it can open the file itself. If it asks for a judgment call, I say "make the call." Most of the time it goes off, reads what it needs, makes the decision, and ships the implementation.

This is the practical version of what I wrote in an earlier post: "**I want the agency to sit on the AI side.**" Don't return judgments — hand judgment over.

What's left at the bottom is the layer where **APIs can't drive things**. Bank accounts, payment review, service signups, billing, API key issuance. That stuff is human-to-human contracts, so I do it myself. Everything else, I push to Claude's side.

## Daily GA4 patrol, with improvement proposals

Here's the new operational pattern that started after launch.

Every day, I have Claude Code patrol GA4 and **surface issues + improvement ideas.** I skim the list and kill the ones that obviously miss. The remaining 60–70% — I have it implement on the spot.

Between the proposal and the implementation, all I'm doing is GO/NO-GO. No coding, almost no design thinking.

I want to make this the operating concept of the brand: "**Ship one improvement, every single day.**" From the moment the store opened, every day something gets a little better. The bet is that a brand whose improvement loop never stops eventually wins.

And 99% of that loop is Claude Code.

## Nothing is organized, but everything is organized

Writing all this out, it hits me: I'm not doing any of the traditional dev hygiene. Organize, design, plan — almost none of it.

No hand-written CLAUDE.md. Sessions on vibes. No routinized workflow. No technical design doc. No task management tool. And yet, from build through operations, it just kind of runs.

To be precise: **the organizing is delegated to Claude.** I don't do it, but Claude Code does. So the organized state gets maintained anyway.

The shape of it feels close to when Masayoshi Son says "let's do it" and a ridiculously competent execution team springs into motion, handles the organizing and the implementation, all of it. **I get to stay on the "let's do it" side, and the execution team is AI.**

The biggest thing I've internalized in the last three weeks is that, in the AI era, an individual can actually reproduce that shape.

## Closing

This is probably not the right way to do it. I'm sure the version where you write a serious CLAUDE.md, split sessions by purpose, and routinize the workflow works fine too.

For me, though, **not organizing was just faster.** If I had time to spend on organizing, I'd rather throw it at Claude Code and spend that time judging what comes back.

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
