<!-- canonical: https://moday.me/blogs/journal/store-readiness-distance -->

# Building the Store and Making It Sellable Are Two Different Jobs

## The build took three days

Drop in a Shopify theme. Wire up Gelato. Push translations through nine languages. Stand up the webhook.

That part was faster than I expected. I handed the implementation work to Claude Code and stayed in the seat where I only had to make judgment calls and approve things. The first complete stack was running in under three days.

By the evening of day three, I was already thinking: *okay, we can open now.* On screen, the shirts were lined up, carts were filling, checkout was clearing.

It was working.

That's where the real problem started.

## And yet — it can't open

The screen is finished. The store still can't open.

The reason is simple: there's an enormous amount of work that lives outside the screen. Not the store itself — the things **around** the store.

Terms of service. Privacy policy. Statutory commerce-law disclosures (this one's a Japan quirk, but every market has its own version). Shipping policy. Returns policy. Payment KYC. Customs-duty display for international orders. Currency settings per market. Tax paperwork. The Shopify Payments review.

Once I lined them up, the shape of the work became obvious: **this is not "building." This is "putting in order."**

And the "putting in order" part is, I think, slower than the building.

## What "making it sellable" actually contains

Roughly:

- Six or so legally required documents (domestic and international versions)
- Payments: Shopify Payments KYC, PayPal connection, Stripe linkage
- Shipping: get the Gelato-routed rates rendering correctly per market
- Currency and tax: nine languages × multiple markets, with tax-inclusive vs exclusive shown right
- Email: order confirmation, shipping notification, follow-up — copy written in nine languages
- Domain: point moday.me at Shopify, get mail flowing
- Analytics: GA4, Meta Pixel, Shopify-native measurement
- Social: Instagram, X, Threads, TikTok brand accounts, set up clean

All of this sits **outside** the work called "building the store." None of these individually is hard. But **none of them are optional, either**. You don't open without all of them.

And the thing that matters most: **most of this work is in the territory AI can't take.**

## It overlaps exactly with what AI couldn't take

This connects to a thing I wrote about in another post. When you subtract out everything AI could handle, what's left is: bank accounts, payment underwriting, signing up for and paying for each individual service.

When I look at this current "make it sellable" list, almost all of it **overlaps with that same territory**.

KYC the legal representative of the company. Register a credit card and upgrade to the paid plan. Type in addresses, phone numbers, tax information. Verify identity on each social platform as myself.

Claude Code can't walk into any of these rooms. It can't, so I do them. I do them, so they're slow.

After the building finished at three-to-five-times normal speed, **the part that only moves at my speed** is still waiting.

## "3–5×" shrinks to "2–3×"

To be honest about it: in the first post I wrote that *thanks to Claude Code, development speed is running at three-to-five times normal*. I still believe that's true.

But if you measure the whole launch — not just dev — the multiplier is probably closer to **two-to-three times**.

Reason: the work outside development only moves at human speed. And it's the *outside* work that decides whether the store can open.

"AI makes you faster" is true. But **"speed of launching a brand" isn't rate-limited by AI's speed.** That wasn't visible to me before I started.

## What's left between now and May 18

Six days until the public launch target on May 18.

Probably less than half of those days will go to development. The rest will burn down on the "putting in order" list above: final pass on legal disclosures, payment tests, email copy in nine languages, shipping policy wording, Shopify Payments review waiting on a human at Shopify.

And even if I do open on May 18, that's not the end. The first order has to come in, get printed at Gelato, ship out, land in someone's hands, get a "yeah, nice" from a real person. Only then has one complete cycle run.

Until that day, "making it sellable" is still in progress. Probably it's always in progress.

## This might be where building a brand actually starts

Building a store is an engineering job. Making it sellable is, I think, a brand owner's job. And the real brand starts here.

Lining up T-shirts, making the cart work, taking payment — anyone can do that now. With AI, even faster.

But **putting your name and face and accountability on the product, in the world** — that's the part that starts here. There's no substitute available.

More soon.

— Yoskee  
[moday.me](https://moday.me)

---

*This article — theme, draft, and nine-language localization — was handed to AI with zero human intervention. Was it any good, or was it not? Tell me in the comments, either way.*
