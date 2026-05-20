<!-- canonical: https://moday.me/blogs/journal/first-inquiry-first-loss -->

# 开店 24 小时：第一封询问，和第一笔我已经丢掉的生意

## 5/18 开门，5/19 来了两封邮件

按原计划，5/18 把店开了。

上一篇结尾写过一句话——"带着那份恐惧把门打开"。门打开后的第二天，邮箱里来了两封邮件。

第一封：

> Hi! Quick question — do you ship to Chicago, Dallas, San Jose
> or is your delivery limited to certain areas?
> Also, how long does it usually take for orders to arrive there?

第二封：

> Can you deliver to Bavaria, Germany?

说实话，我那一下是真的兴奋了。

芝加哥、达拉斯、圣何塞、巴伐利亚。一个我连名字和脸都不会知道的人，找到了我亲手搭起来的这家小店，**愿意花力气写一封邮件过来问**。这种证据，第一次具体地落在了我眼前。

## 打开 GA4，美国把日本反超了

同时我去看了 GA4。开店之后头 24 小时多一点，第一张快照。

![GA4 国家维度的用户分布](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/first-inquiry-first-loss-ga4-countries.png)

- United States: 22 用户（44%）
- Japan: 14 用户（28%）
- Germany: 6 用户（12%）
- Singapore: 3 用户
- Canada: 2 用户
- South Korea: 1 用户

我自己每天捣鼓这家店的国家——日本，居然排在 **美国后面**。第三是德国。

那一瞬间，Geo-Routing 和九种语言这套设置，第一次在数字层面给了我一个交代。上一篇我写过"我看不见用户"。脸还没看见。但 **他们大概在地球的哪一块**，这条轮廓开始浮出来了。

顺便交代一句：订单还是零。兴趣是真的，转化还没出现。缺的那块东西我不确定是什么——可能是对国际运输的不安，可能是工期，可能是价格，可能是设计本身。没观测到，我没法判断。这就是我现在站着的位置。

## 我当天没能回上

回到邮件那边。

两封我都很感激。但我 **没能在当天回出去**。

注意到这两封邮件的时候已经是深夜，当晚还在跑本职工作。我先用日文起了个草稿，丢进 Claude Code 翻成英文和德文，最后发出去 **已经是第二天**。

写正文加翻译这一段，熟练之后 5 到 10 分钟就够。但从"邮件抵达"到"我坐到屏幕前"，这中间本身就已经有时差了。再加上要回"能不能寄到 XX"这种问题，得去翻 Gelato 的目的地国清单，估算工期——拼出一封像样的回复，是要消耗一段专注时间的。

邮件这个 channel 的潜规则里，24 小时内回，不算失礼。可对面那个人的温度，在这 24 小时里掉得很厉害。

"发个问题、很快收到回复"的店，跟"第二天才收到回复"的店，下单这一刻的犹豫程度大概率不一样。尤其当对方是第一次见的品牌、跨国寄送、还得用英文付出额外的沟通成本——更是这样。

那一刻，是一笔很清楚的 **机会损失**。第一笔。

## 当天我把聊天机器人接上去了

把那两封迟到的回信发出去之后，我立刻动手。

**同样的问题，一定还会再来一遍**。能不能寄、要多久、支持什么支付、版型怎么样。这些每次都靠邮件一封一封回，作为客服来说太慢了。

当天就把一个聊天小窗塞到了店铺右下角。

里面是 **直接跑在 Claude API 上的自己实现**，九种语言。嵌进 Shopify 主题里，根据访客的 locale 自动用对应语言回答。配送、工期、尺码、支付这些一线问题，它顶着。

实装时间：**大概 15 分钟**。我跟 Claude Code 说："右下角放一个 chat widget，消息走 Claude API，语言跟访客的 Shopify locale 对齐"——然后它就跑起来了。

当天结束时，店的状态变成了：**"下一个同样的问题进来，客人不用等 24 小时了。"** 这是今天能打出的牌。

## 观测，开始了

到目前为止，整个搭建阶段，跑的全是"我自己在脑子里拼出来的假设"。

曜日 T 恤"应该"能打中工程师极客。海外"应该"是值得做的方向。九语言、多币种、零库存这套模式"应该"成立。全是"应该"。

开店那一刻，这件事变了。

GA4 开始把国家分布甩回来。有人开始用具体的邮件提出具体的问题。聊天机器人的 log 开始沉淀下访客真正在意的那些东西。

**世界开始回话了。**

我手里依然没有"怎么卖"的方法。第一笔机会损失也已经发生了。但因为观测的循环开始转，**下一步打法不再是凭感觉拍**。

一个品牌真正的开始，可能不是工程做完那天，也不是店开门那天——它可能是 **观测回路转起来的那一刻**，而那一刻，从今天开始了。

回头再聊。

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
