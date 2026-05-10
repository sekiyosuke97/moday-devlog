<!-- canonical: https://moday.me/blogs/engineering/tech-stack-selection -->

# Building MODAY's Tech Stack — I Handed It All to Claude, and Now I'm Using Services I've Never Heard Of

## This brand's concept is "AI-driven brand launch"

Let me set the stage first. MODAY's business concept is about **"how far we can push AI-driven brand launches"** — honestly, that's almost half the point. Selling T-shirts is secondary.

I do EC consulting for a living and I've seen enough of the real-world work. But here's the constraint: **one person, global reach, three days to launch**. I'm experimenting with how much I can actually hand off to AI — both the thinking and the implementation.

So that's how I approached the tech stack selection too. Not "I don't know, so I asked AI," but rather **"I'm throwing this at AI from the start — I'll just set the decision criteria, and let it do the rest."** Clean division of labor.

Here's what we ended up with:

| Layer | Tech |
|---|---|
| Store | Shopify (Dawn theme) |
| POD | Gelato |
| Translation | Translate & Adapt |
| Automation | Make.com |
| Webhook | FastAPI on Render.com |
| Image Generation | fal.ai FLUX Pro |
| AI Text Processing | Anthropic API |

Out of all that, **I'd only heard of Shopify and Anthropic API**. Everything else? First time seeing those names, straight from conversations with Claude.

It's only been three days since I picked this stack and started building it.

## I chose Shopify because of a news headline, not the tech

Simple story here.

I saw a news piece about **Shopify MCP** a while back. I thought, "Oh, that means Claude Code can actually build stores with this." That was basically it.

I do EC consulting normally, so I've looked at Shopify from the outside. But I'd never really built with it myself. Still, I figured "if Claude Code can touch Shopify through MCP, I can survive not knowing it well."

I didn't even consider domestic services (BASE, STORES) from the start. One reason: **I wanted to go global from day one**. Nine languages, multiple currencies, multiple payment methods. Only Shopify showed all of that right out of the box.

Honest truth? My selection axis wasn't "technical specs." It was **"does it play nice with Claude Code?"** and **"can I sell this to the world?"**

## POD was always going to Claude from the start

How do you manufacture and ship T-shirts?

I didn't know a single POD (Print On Demand) service. Never heard of Printful, Printify, Gelato — nothing.

But that wasn't a problem. **I was planning to hand this off to AI anyway**. My knowledge of the global POD market is limited. So instead of me trying to compare them myself, I'd give Claude the criteria and let it do the selection.

Here's what I asked:

> I want to sell custom T-shirts on Shopify using on-demand printing, fully automated. Target markets are global — America, Europe, Asia — with Japan as secondary. Which on-demand print service should I use? Can you research it?

That's it. **All business-layer criteria**. "Global," "automated," "Japan is secondary." I didn't — couldn't — throw in technical axes like SDK language, rate limits, Webhook format, or auth methods.

What came back:

> For global on-demand print, I've compared the three main services. Bottom line: **Gelato is the best fit for your use case**.
>
> **🥇 Gelato (Recommended)**
> - Local printing network with 140+ facilities across 32 countries
> - Local production available in Japan, South Korea, Singapore, Malaysia, Australia, India, China
> - Average delivery to EU, US, Asia customers within 72 hours
> - Low tariff risk (local production means no cross-border shipping)
> - Ships to 200+ countries
> - Weaknesses: Smaller product lineup than Printify, slightly higher prices
>
> **🥈 Printful (If brand quality matters most)**
> - 17 facilities across North America, Europe, Asia
> - Strict quality control, good for brand building
> - Weaknesses: Most expensive of the three
>
> **🥉 Printify (If cost matters most)**
> - Network of 90+ print providers, 950+ product options
> - Often 10-20% cheaper than Gelato
> - Weaknesses: Fewer local production hubs in Asia than Gelato, no Japanese support
>
> **Recommended approach:** For global focus with Japan secondary, use Gelato as your main. You get local production everywhere (US, Europe, Asia), which beats the competition on shipping costs, tariffs, and speed.

Decision made. **I'm handing the core of my store to a POD service I've never met or touched.**

If I did this comparison myself as a consultant, I'd be reading through three sets of docs, consulting with people, and burning a week easy. This was near-instant.

## FastAPI? I'm still not even sure what it does

Look at that tech stack table again. "Webhook: FastAPI on Render.com."

I have to laugh at myself a little. **I still don't really understand what FastAPI is.**

Early on in the build, I needed something to receive order webhooks from Shopify and pass them to Gelato. Claude Code said, "I'll write this in FastAPI and deploy it to Render.com." My understanding: it's a Python framework. My response: "Please do."

It got written. It got deployed. It works. The most I've done is watch logs in the Render dashboard.

By the way, **that setup isn't even in use anymore**. Something felt off while building, so I switched approaches. I'll write about that in the next article or the one after.

When you commit to "AI-driven," **you can't necessarily explain your entire stack yourself**. I'm okay with that. It's a known trade-off.

## Is this smart, or is this dangerous?

I'm not even sure how to answer that yet.

The upsides are obvious:

- Options I'd never have known about get considered from day one
- "My technical skills" stops being a blocker
- Design and implementation happen in parallel instead of sequentially — what would take a week happens instantly
- A solo non-engineer can actually build a global D2C business

The risks are just as obvious:

- If something breaks, I might not be able to figure out what's happening
- I can't explain "why" behind each choice (which is why I'm writing this now, to figure it out)
- If a vendor dies, I might be slow to pivot

How that trade-off plays out in six months? No idea yet. While it's running, it's magic. If it stops, I might be in trouble.

I'm doing this anyway because I want to **actually measure how far AI can go — using a real business, not a side project**. That's the only way to get a real answer. Real money moving, real customers buying, real shipments going out — that's where you learn whether this works or breaks.

## Three days of stack building. Now we're selling to the world.

Three days since I picked this stack and started assembling it.
The actual build time was shorter than that.

In those three days, the store went live. Nine languages are translating. Order webhooks are firing. Product syncing to Gelato started working. **This is the first iteration of the "AI-driven brand launch" experiment.**

I'm pretty sure half this stack gets swapped out in six months. FastAPI / Render is already gone. There are other sketchy pieces.

But right now, today, this moment — that's when we're getting ready to sell to the world. And that's what matters most.

Next, I'll write about how to actually separate "what Claude Code did" from "what humans did."

— Yoskee
[moday.me](https://moday.me)