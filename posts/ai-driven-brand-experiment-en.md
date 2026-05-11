<!-- canonical: https://moday.me/blogs/engineering/ai-driven-brand-experiment -->

# Four Things I Still Can't Hand to AI

I'm building MODAY — a one-person, day-of-the-week T-shirt brand — and I'm trying to hand every single task to AI. Three days in, four things refused to move.

## The actual reason I'm doing this

You've probably read the obvious half of why this brand exists: a Japanese "I'm sorry" T-shirt going viral, days of the week blurring under remote work. That's the surface.

The other half is harder to admit out loud — I want to figure out how to build companies in the AI era before everyone else does.

My day job is e-commerce consulting. I see plenty of operations from the inside. So when generative AI broke open a couple of years back, one question started gnawing at me and never stopped: how much of a business can you actually let AI run?

Reading didn't answer it. Twitter didn't answer it. Papers didn't answer it. The question doesn't surrender to reading — it surrenders to a real business with real money moving through it.

So MODAY is a brand, yes. But it's also a one-person experiment at the right scale to actually measure things. Zero inventory. Solo operator. Global from day one. Three days to launch. Real money, real customers, real packages. Hobby projects and internal pilots let your judgment go soft. You can't measure anything without skin in the game.

The rule: no lines. Hand off everything. See what won't move.

## Three days in, zero regrets

I haven't had the "I shouldn't have let AI do that" moment yet. Not for stack selection. Not for the design system. Not for the store, the webhooks, the translations, the copy. I've shipped Claude's output almost as-is across the entire build.

That sounds like a flex. It isn't. The honest read is darker — I've also handed Claude my judgment criteria. There's nothing left in me to regret with. If I'd kept my own opinions, eventually a "wait, I would've gone the other way" moment would arrive. It hasn't.

For better or worse.

## And yet — four things stayed mine

For all the no-lines talk, four parts of this build refused to be delegated. By subtraction, here they are.

**1. The decision to send a prompt at all.**

The first sentence I type to Claude — "what's next?" — still comes from me. Every single time. I can't make it not.

When I can hand this off, I'll be at the next stage. I'm not there.

**2. Bank accounts and payment processor approval.**

Shopify Payments KYC. Stripe identity verification. Opening accounts for international payouts. These don't accept anything but a human. You show up with an ID, sign with your name and your face, and become the legal counterparty.

**3. Service signups and putting a card on file.**

Gelato. Render. fal.ai. Make.com. Anthropic. For each one I create the account, enter the card, and click "upgrade to paid." Every signup is my hand on the dashboard.

**4. Generating the API key — up to the moment of handoff.**

For Claude Code to call an API, the key has to exist. The "create new key" button is mine. The moment the key lands in `.env`, it stops being mine.

That's the entire list. Across three days, those are the only points where my hand physically moved. Everything else, Claude is running.

## I want to hand off #1 too

Of the four, the one I most want gone is the first — the decision to prompt at all.

The version I'm aiming at: Claude Code shows up with "here's what we're doing next," I answer yes or no, and the direction of the business itself migrates fully to the AI side.

This is probably already possible technically. An agent setup can self-decompose tasks, implement them, and propose the next one in a loop. Plenty of builders are running variants of this today.

I haven't gone there yet at MODAY's stage. Part of me still wants to choose the direction of the first step. Honestly, that's the whole thing. Letting that go is my next move.

## The other three aren't AI's limit. They're the system's.

This is the line I most wanted to write.

The bank, the KYC, the signups, the API keys — none of these stayed with me because "AI lacks the judgment." That's not why.

The real reason is institutional. AI has no legal personhood. Not as an individual. Not as a corporation. It cannot be a party to a contract. That's it.

Technically, Claude Code with browser automation could probably do all of these tomorrow. Fill the form. Upload the ID photo. Click the email link. Computer Use already exists. The blocker isn't capability.

The blocker is that even if Claude did the clicks, **the registered party would still be me.** Claude would just be filling forms under my name. The liability stays with the human.

So those three aren't where AI hits its limit. They're where society's institutions haven't caught up. The day AI itself can be the legal operator of a business, those three will move too.

## Subtraction, not segregation

The "what humans do vs what AI does" framing will look obsolete in three years.

The moment you draw the line — "humans here, AI there" — the line becomes a constraint. And the question "how far can AI actually go?" becomes unanswerable from inside that constraint. You can't measure the limit if you've defined the limit upfront.

So MODAY isn't segregation. It's an attempt to hand off everything and check, by subtraction, what wouldn't move.

Four things stayed. Three are institutional. One is my own intent.

Time fixes the three. The one — I have to let go of that myself.

More soon.

— Yoskee  
[moday.me](https://moday.me)
