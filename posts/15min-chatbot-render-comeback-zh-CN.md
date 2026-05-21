<!-- canonical: https://moday.me/blogs/journal/15min-chatbot-render-comeback -->

# 15 分钟搭好的客服 bot —— 把 Render 扔了，又捡了回来

## 从 5/19 的机会损失，到 15 分钟后跑起来

另一篇里写过，5/19 那天来了头两条咨询。
当天没回上，回复发出去已经是第二天。
我把这件事定性成 **机会损失**，当天就把客服 bot 做了出来。

就是店铺右下角那个常见的小窗口。
从动手到部署上 Shopify、开始接客，前后大约 15 分钟。
里面的事，凭我自己掌握的程度记一下。

## 整体结构

大致是这样：

- **前端**：Shopify 主题里塞一个右下角的小窗口（具体怎么实现的我没去搞清楚）
- **后端**：Render.com 上跑一个服务，去调 Claude API
- **语言**：跟着 Shopify 的 locale 走，9 种语言
- **历史记录**：写到 Google 表格里
- **升级路径**：答不上来的问题，引导到联系表单

设计思路就一句话，**能简单就简单**。
个人事业这个阶段，不管做什么，都不想给自己背一堆复杂的东西。

## 把 Render 扔了，又捡了回来

另一篇里我宣布过「**FastAPI / Render 已经下线了**」。
看上去有点自相矛盾，但下线的是 **Webhook 那条线**。
原来 Shopify 的订单 webhook 进来、再丢给 Gelato 的流程，是跑在 Render 上的 FastAPI 里。
那一块我用别的方案替掉了（这个过程能单独写一篇，回头再说）。

客服 bot，是把 Render **换了个用途，又重新跑起来**。
以前是当 Webhook 服务器用，现在是当 bot 的 API 后端用。
角色完全不一样，是另一个服务、另一个进程。
只是恰好跑在同一家 Render 上。

「把 Render 扔了」和「在用 Render」，两件事不冲突。
**每个用途、在那个时间点，重新挑一遍最合适的工具** 就行。
要是被以前的判断绑住、决定「以后再也不用了」，脑子就僵了。

判断的尺子在我手里。具体怎么搭，交给 Claude Code。
每次重搭，都去拿一次当下的最优解。

## 历史记录写进 Google 表格

bot 和用户之间的所有对话，全部写到 Google 表格里。
时间、locale、用户提了什么、bot 怎么答的、有没有走升级路径。

这是 Claude Code 自己提的方案，我同意了。
事后想想，正好有三个理由特别合适。

1. **不想专门起一个数据库**：要设计 schema，要付运维费，可视化还得另外搞。对个人事业阶段太重
2. **白嫖就够**：有个 Google 账号就行，零成本
3. **以后让我自己或 Claude Code 分析的时候，两边都能直接读**：列一拉就明白

尤其是第 3 点关键。
以后我跟 Claude Code 说「**帮我把最近的咨询趋势整理一下**」，
它就能直接去读那张表。
如果是数据库，还得写抽取脚本、导成 CSV，多绕一道。

要专门做个数据库当然更干净，但现在这个体量，表格已经够用。
个人事业阶段，这种程度的 **「正确的偷懒」**，我觉得是对的。

## 9 种语言怎么处理

把 Shopify 当前的 locale 取出来，传给 bot。
bot 在调 Claude API 的 prompt 里加一句「**请用这种语言回复**」。
中间不插翻译步骤。Claude 直接用对应的语言写。

另一篇里我写过「不是翻译，是本地化重写」，这套逻辑对 bot 同样适用。
不是先用日语写一遍、再翻成英语，而是从一开始就按英语母语者的语感来答。
是德语就按德语母语者来答。
全程在模型里跑完，翻译的延迟、误译的风险，结构上都减掉了。

这件事我也没干什么特别的。
只是丢了一句「**接住 Shopify 的 locale，按那种语言回复**」给 Claude Code。

## prompt 里写了一句「把站点信息吃透」

bot 要能回答 MODAY 站点上的信息，以及 Gelato 的商品信息。
能不能发货、交期、尺码、支付方式、退货政策、价格、套装组成。

我跟 Claude Code 说，「**把这些吃透**」。

老实写一下：**它到底是怎么吃透的，我自己也没搞清楚**。
是埋进 prompt 里了、还是去 fetch 站点了、
还是两个一起用，这些都是 Claude Code 自己定的、自己写的。

跟另一篇说的一样，指令我给，实现交出去。
现在它跑得动、答得也像回事，目前这样就够。
真坏了，我就跟 Claude Code 说「修一下」。

## 答不上来的，引导去联系表单

什么问题 bot 都直接拍胸脯答，是危险的。

特定尺码的个别咨询、礼品包装、企业订单、出问题的处理。
这些要是 bot 一口咬定，后面就会对不上。

bot 判断「这个最好别答」的时候，就把人引导到联系表单。
护栏的设计，也是丢给 Claude Code 的。
我做的只是丢一句「**答不上来的问题，引导到联系表单**」。

哪些问题 bot 自己答、哪些要升级，
那条边界线是 Claude Code 自己画的。
偶尔看看日志，要是有明显分错的我再调，
但目前没出现。

15 分钟能跑起来，是因为那 15 分钟里要想的事不多。

「右下角小窗口」「基于 Claude API」「9 种语言」「Render 复活」「记录写表格」
「答不上来引到联系表单」。
这几条定下来，剩下的 Claude Code 自己写。
我负责拍板，再确认能不能跑。

店铺开张第二天，客服自动化的底座就跑起来了。
**「一天改进一个」**，头一个就是这玩意儿。

那么，下次再写。

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
