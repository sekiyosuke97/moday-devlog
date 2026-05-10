<!-- canonical: https://moday.me/blogs/engineering/tech-stack-selection -->

![MODAY engineering hero](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/assets/tech-stack-selection-hero.png)

# I Asked Claude to Pick My Tech Stack — Now I'm Running on Services I'd Never Heard Of

## The brand's thesis is "how far can AI take a launch?"

Up front: MODAY is half a T-shirt brand and half an experiment.

The real question I'm trying to answer is **how much of a brand launch can I delegate to AI?** I work as an e-commerce consultant by day, so I've watched the operational side of launches up close. But MODAY is a deliberate setup: one person, global market, three days, and AI doing as much of the judgment and execution as it'll let me hand over.

The tech stack got picked the same way. Not "I didn't know, so I asked AI." More like: **I started with the assumption that AI would pick, and my only job was to define the criteria.**

Here's what came out:

| Layer | Service |
|---|---|
| Storefront | Shopify (Dawn theme) |
| Print-on-demand | Gelato |
| Translation | Translate & Adapt |
| Automation | Make.com |
| Webhook server | FastAPI on Render.com |
| Image generation | fal.ai (FLUX Pro) |
| Text / AI processing | Anthropic API |

Of those seven, **the only names I recognized going in were Shopify and Anthropic.** The rest I met for the first time in conversations with Claude.

The whole stack is three days old.

## I picked Shopify because of a news headline

The Shopify decision is the dumbest one to explain.

A while back I saw the Shopify MCP announcement go by. My immediate thought: "ok, so Claude Code can actually drive a Shopify store now." That was 90% of the decision.

I've watched Shopify from the consultant side for years, but I'd never built on it myself. Doesn't matter — if Claude Code can reach in via MCP, I figured I could ship without having to first become a Shopify person.

Japanese-domestic platforms (BASE, STORES) never made the shortlist. One reason: **I wanted to ship globally on day one.** Nine languages, multi-currency, real cross-border checkout. Shopify is the only platform that makes that look easy on day one.

So my actual selection criteria weren't "which platform is technically best." They were "which one works smoothest with Claude Code" and "which one lets me sell worldwide tomorrow."

## I outsourced the POD decision to Claude on purpose

How do I print and ship the actual T-shirts?

Going in, I knew zero print-on-demand services. Printful, Printify, Gelato — never heard of any of them.

That wasn't a problem. **The plan was always to outsource the selection.** My personal knowledge of the global POD market is shallow. If I write down the business constraints and let Claude rank options against them, the answer is going to beat anything I'd reach on my own in a week of research.

The prompt I sent:

> I want to sell custom T-shirts via Shopify with print-on-demand, fulfilled automatically. Target markets are the US, Europe, Asia — Japan is a secondary market. Which POD service should I use? Compare a few.

That was it. **Nothing technical.** No SDK languages, rate limits, webhook formats, or auth schemes. I couldn't have written those criteria if I'd tried.

The answer:

> I compared the three major POD services. Bottom line: **Gelato is the best fit for your use case.**
>
> **🥇 Gelato (top pick)**
> - Local print network in 32 countries, 140+ facilities
> - Local production in Japan, Korea, Singapore, Malaysia, Australia, India, China
> - Average 72-hour delivery to EU / US / Asia customers
> - Low customs risk (production stays in-country)
> - Ships to 200+ countries
> - Trade-off: smaller catalog than Printify, slightly higher unit cost
>
> **🥈 Printful (best for brand)**
> - 17 facilities across NA, EU, Asia
> - Tightest QC of the three; well-suited to brand-building
> - Trade-off: highest unit cost
>
> **🥉 Printify (best for cost)**
> - 90+ print providers, 950+ products
> - 10–20% cheaper than Gelato in most categories
> - Trade-off: thinner Asian local-production network, no Japanese-language support
>
> **Recommendation:** for global-primary, Japan-secondary, lead with Gelato. Local production across all three regions wins on shipping cost, customs, and delivery speed simultaneously.

Decided. **The core of my fulfillment now runs on a service I'd never heard of and never touched.**

If I'd done this comparison the way I would have as a consultant — reading three sets of docs, asking around — I'd have spent a week. Instead, near-instant.

## With FastAPI, I'm not even at the "do you use it?" level

The stack table says "Webhook: FastAPI on Render.com."

I laugh a little when I write that. **I don't actually know what FastAPI is.**

Early in the build I needed something to catch Shopify order webhooks and forward them to Gelato. Claude Code said "I'll write it in FastAPI and deploy it to Render." A Python framework, apparently. I said go ahead.

It got written. It got deployed. It works. My total interaction with it is staring at logs in the Render dashboard.

(Side note: that piece is **already retired.** Something felt off mid-build and I swapped it out for a different approach. That's two posts down the road.)

When you decide to "go AI-first," **you accept that you can't fully explain your own stack.** That trade-off is the point, not a bug.

## Smart, or reckless?

Honestly, I haven't sorted out which.

The upside is clear:

- Options I'd never have considered show up on the shortlist on day one
- "What I personally know" stops being a ceiling
- Decision and implementation collapse into the same step — selection that should take a week happens immediately
- A non-engineer running a global D2C brand becomes a real, not theoretical, project

The downside is just as clear:

- When something breaks, I might not be able to read what's broken
- I can't yet explain "why this stack" in my own words (that's literally why I'm writing this post)
- If a vendor dies, my replacement decision is going to be slow

I won't know how this trade plays out for another six months. While it works, it's incredible. The day it stops working might be brutal.

The reason I'm running it this way anyway: **I want a real answer to "how far can AI go?" measured against a real business.** Hobby projects don't generate the answer. Real money, real customers, real shipping is what produces a number you can trust.

## A three-day stack, going global

It's been three days since I picked this stack and started building. The actual hands-on-keys time is shorter than that.

Inside that window, the storefront went live, nine languages started flowing, the order webhook is firing, and Gelato product sync is moving. **This is the v1 stack of an "AI-first brand launch" experiment.**

Half of it will probably be replaced by year-end. FastAPI/Render are already gone. There are other suspect spots.

But as of today, this stack is on the brink of selling globally — and that's the part that matters.

Next post: which work I handed to Claude Code, and which work I had to do myself.

— Yoskee
[moday.me](https://moday.me)

