<!-- canonical: https://moday.me/blogs/journal/first-inquiry-first-loss -->

# 24 Hours After Opening: The First Inquiries, and the First Sale I Already Lost

## Opened on 5/18. Two emails on 5/19.

I opened the store on 5/18, as planned.

The last post ended with "opening with the fear still attached." The day after I opened, two emails came in.

The first:

> Hi! Quick question — do you ship to Chicago, Dallas, San Jose
> or is your delivery limited to certain areas?
> Also, how long does it usually take for orders to arrive there?

The second:

> Can you deliver to Bavaria, Germany?

I'll be honest: I was *thrilled*.

Chicago, Dallas, San Jose, Bavaria. Someone whose name and face I'd never know had found their way to the store I'd built, and was interested enough to **decide to send an email**. That kind of evidence landed in front of me for the first time.

## I opened GA4. The US was outranking Japan.

In parallel, I checked GA4. The first 24-hour snapshot since opening.

![GA4 users by country](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/first-inquiry-first-loss-ga4-countries.png)

- United States: 22 users (44.9%)
- Japan: 13 users (26.5%)
- Germany: 6 users (12.2%)
- Singapore: 3 users
- Canada: 2 users
- South Korea: 1 user

The country I live in, the one I poke at the store from every day, ranks **second to the United States**. Germany comes in third.

That was the moment the geo-routing and the nine-locale setup paid off — for the first time, in numbers. In the last post I wrote, "I can't see the customer." The face still isn't in focus. But the **rough geography of where they are** has started to surface.

For the record: orders are still zero. Interest is real, but it isn't converting yet. Something is missing — anxiety about shipping, lead time, price, the look. I don't know which yet, and I won't know until I can observe it. That's where I am right now.

## I couldn't reply the same day.

Back to the emails.

Two of them came in. I'm grateful. But I **couldn't reply the same day they arrived**.

I noticed them late at night, and I had day-job work running that evening. I drafted the Japanese reply, ran the translations through Claude Code into English and German, and the messages actually went out **the next day**.

The drafting + translating part itself is 5–10 minutes once you're set up. But the latency from "email arrived" to "I'm in front of the screen" already adds delay. On top of that, answering a shipping-availability question means checking Gelato's covered countries, estimating lead times — assembling a real reply takes a chunk of focus.

For email as a channel, replying within 24 hours isn't considered rude. But the temperature on the other side drops a lot in 24 hours.

The difference between a store where "you send a question and a reply comes back fast" and one where "the reply comes the next day" probably changes a purchase decision. Especially when it's a first-time brand, ships internationally, and the customer paid the cost of writing in English.

That was a clear **opportunity cost**. The first one.

## So that same day, I shipped a chatbot.

After I sent out the late replies, I moved fast.

**The same questions are going to come again.** Shipping availability, lead time, payment methods, sizing. Answering these one-by-one over email is too slow as support.

That same day, I dropped a chat widget into the bottom-right of the store.

It's **built on the Claude API directly**, with nine-language support. Embedded in the Shopify theme, it responds in the visitor's locale automatically. First-line answers for shipping, lead time, sizing, and payments now live there.

Build time: **about 15 minutes**. I asked Claude Code, "put a chat widget bottom-right, route messages through the Claude API, match the language to the visitor's Shopify locale" — and it worked.

The state of the store at the end of that day: **"if the same question comes in next, the customer isn't waiting 24 hours."** That was the move available that day.

## The observation loop started.

Up to this point, the whole build phase ran on "hypotheses I'd assembled inside my own head."

The day-of-the-week tee should land with engineers and geeks. International should make sense. The nine-locale, multi-currency, zero-inventory model should work. All of it was "should."

That changed the moment I opened.

GA4 starts returning country breakdowns. Someone sends a specific question by email. The chat logs start collecting what visitors are actually anxious about.

**The world has started to reply.**

I still don't have "a way to sell." The first opportunity cost already happened. But because the observation loop has started, **the next move isn't a guess anymore**.

The real beginning of a brand might not be when the engineering is done, or when the store opens — it might be when **the observation loop starts spinning**, and that's the part that began today.

More soon.

— Yoskee  
[moday.me](https://moday.me)
