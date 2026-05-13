<!-- canonical: https://moday.me/blogs/journal/store-readiness-distance -->

# Building the Store and Making It Sellable Are Two Different Jobs

## The build took three days

Drop in a Shopify theme. Wire up Gelato. Push translations through nine languages. Stand up the webhook on Render. Done.

That part was faster than I expected. I handed implementation to Claude Code and stayed in the seat where my only job was making judgment calls and pressing "approve." The first complete stack was running in under three days.

By the evening of day three I was already thinking: *okay, we can open now.* On screen, the shirts were lined up, carts were filling, checkout was clearing. A real-looking US-dollar order would walk through to Stripe sandbox without a hitch.

It works.

That's where the actual problem started.

## And yet — it can't open

The screen says done. The store still cannot open.

The reason is simple: there's an enormous pile of work that lives outside the screen. Not the store itself — the things **around** the store.

Terms of service. Privacy policy that satisfies CCPA and GDPR at the same time. Shipping policy that holds up against Section 5 of the FTC Act on deceptive practices. Returns policy. KYC for Shopify Payments — they need an EIN, a bank account in the merchant's name, and a beneficial-owner declaration. Customs duty display and HS code mapping for international orders. Per-market currency. Sales tax registration in any US state where you cross economic nexus (Wayfair v. South Dakota changed the rules, and most platforms now collect on your behalf — but you still need to file). The Shopify Payments review itself, which can sit on a human's desk for a week.

Once I lined them up, the shape became obvious: **this is not "building." This is "putting in order."**

And the putting-in-order part is, I think, slower than the building.

## What "making it sellable" actually contains

Roughly:

- **Legal copy:** Terms, Privacy (CCPA + GDPR), Shipping, Returns, Cookies — five-plus documents, each version-controlled per jurisdiction
- **Payments:** Shopify Payments KYC (EIN, bank, beneficial owner), PayPal Business linkage, Stripe as fallback
- **Shipping:** Gelato's print-on-demand rates surfaced correctly per destination, with HS codes for cross-border
- **Tax:** US sales tax nexus by state (Shopify Tax handles most of this now, but the registrations are on me), VAT in EU, OSS/IOSS for low-value EU shipments, JCT for Japan
- **Email deliverability:** SPF, DKIM, DMARC set up on moday.me; transactional templates rewritten in nine languages
- **Domain:** moday.me pointed at Shopify; mail flowing without Gmail flagging us
- **Analytics:** GA4, Meta Pixel, Shopify-native — and the consent banner that has to gate them
- **Social:** Instagram, X, Threads, TikTok brand handles, each verified with the founder's ID

All of this lives **outside** the work called "building the store." None of it is individually hard. **None of it is optional, either.** You don't open without all of it.

The thing that matters most: **most of it is in the territory AI can't take.**

## It overlaps exactly with what AI couldn't take

This connects to a thing I wrote in an earlier post. When you subtract out everything AI can handle, the residue is: bank accounts, payment underwriting, signing up for and paying for each individual service.

Looking at the current "make it sellable" list, almost all of it **overlaps with that same territory**.

KYC the company's beneficial owner. Register a credit card and upgrade to the paid plan. Type in EIN, business address, phone, the W-9 equivalents. Verify identity on each social platform as a real human with a real face.

Claude Code can't walk into any of those rooms. It can't, so I do. I do, so it's slow.

After development finished at three-to-five-times normal speed, **the part that only moves at my speed** is still waiting.

## "3–5×" collapses to "2–3×"

To be honest: in the first post I wrote that *thanks to Claude Code, development speed is three-to-five times normal*. I still think that's true.

But measured across the whole launch — not just the build — the multiplier probably collapses to **two-to-three times**.

Reason: the work outside development only moves at human speed. And it's the *outside* work that decides whether the store can open.

"AI makes you faster" is true. **"Speed of launching a brand" is not rate-limited by AI's speed.** That wasn't visible to me before I started.

## What's left between now and May 18

Six days to the public launch target.

Probably less than half of those will go to development. The rest burns down on the list above: final legal-copy pass, payments smoke tests, email copy in nine languages, shipping wording, and waiting on a human inside Shopify Payments to clear the review. Nothing about that queue moves faster because I want it to.

And even if I do open on May 18, that's not the end. The first order has to come in, get printed at Gelato in the customer's region, ship out, land in someone's hands, and earn a "yeah, nice" from a real person. Only then has one full cycle run.

Until that day, "making it sellable" is still in progress. Probably it's always in progress.

## This might be where building a brand actually starts

Building a store is an engineering job. Making it sellable is, I think, a brand owner's job. The real brand starts here.

Lining up shirts, making the cart work, taking payment — anyone can do that now. With AI, even faster.

But **putting your name and your face and your accountability on a product that ships into the world** — that starts here. There's no substitute available.

More soon.

— Yoskee  
[moday.me](https://moday.me)

---

*This article — theme, draft, and nine-language localization — was handed to AI with zero human intervention. Did it land or didn't it? Tell me in the comments, either way.*
