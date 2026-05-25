<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# 为了做短视频，我把不懂的全甩给了 AI

## 上一篇说的"观测回路"，我先收回

之前那篇里我写过——"观测回路开始转了"。开店那一刻起，世界开始回话。

开店第四、第五天，我搞明白一件事：**样本量根本不够，谁也观测不到。**

GA4 我盯着看，购物车行为我跟着追，聊天机器人的 log 我也翻——可量太小，啥假设也立不起来。要想真开始推理，**得先把人弄进来。**

所以现在该做的不是观测，是**先把流量搞上去**。顺序我一开始就搞反了。

## 这次得亲自下场拉客了

整个搭建阶段，我都在**造机器**这件事上死磕。九语言十平台分发、聊天机器人自动化、下单到生产的自动化、改善回路的自动化。全是"先把系统搭好，剩下让它自己跑"的逻辑。

拉客这事我本来也想这么干——投点广告预算 → 数据进来 → AI 给改善方案 → 把回路自动化 → 收工。

可是上一篇也讲过，现在没广告预算。投放走不了，**就只剩自然流量这条路**。特别是短视频——我这商品本身视觉冲击就足，这个格式应该是匹配的。

但有个问题：**短视频现在在火什么，我是真的一点不懂。**

中文短视频我都没在认真追，更别说英文圈的短视频。我本职是电商顾问，这块只能老实承认是软肋。我现在踩的是自己不擅长的地方，这点我心里有数。

## 第一步：去问 Gemini

正好那阵子在刷 Google I/O 的消息，也想找个理由把 Gemini 试一遍。于是丢了个问题过去：「面向英语圈商务人群的短视频，现在 TikTok / LinkedIn / Shorts 上流行什么趋势？」

回来的东西，对我来说是个完全陌生的世界：

- **Corporate Buzzword Satire**——讽刺职场黑话的小品："Synergy"、"Circle back"、"Let's take this offline"，这些虚得不行的词被一通调侃。
- **自嘲版的 "Day in the Life"**——比如"怎么不下床还让 Teams 显示 Active"，把那种螺丝钉的无力感拿来开自己玩笑。
- **Corporate Erin 系**——演冷血 HR 的角色，职业假笑加快语速，把裁员通知包装得像在念欢迎词。
- **LinkedIn Lunatics**——把 LinkedIn 上那种被诗化了的"职场感悟"截下来，搬到 TikTok 上一字一句念出来嘲讽。

Gemini 给我提炼出来的共通点，扎得很准：英语圈职场幽默能病毒传播的内核，是**"用幽默对荒唐企业文化进行的喜剧式造反"**。

这片地，刚好就在 MODAY 的隔壁。"MONDAY: System Booting…"和"FRIDAY: Build Successful ✓"这种 T 恤的世界观，本来就活在这种文化里。

要是只靠自己脑子里转，我这辈子也想不到那四个题材。

## 第二步：把素材丢给 Codex 画分镜

Gemini 给的东西，我原封不动塞给了 Codex。Prompt 是这样："给 MODAY 写一条用来拉客的短视频分镜，9:16 竖屏 22 秒，受众是英语圈商务人群，调性是讽刺和幽默，结尾落到品牌。"

回来的是这个：

![分镜：Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

**"Weekdays Ranked by Developer Damage"**——把一周七天，按对开发者的伤害值排个名。不是产品种草，是一条**能自己立得住的 meme**。结构上就是让评论区为了排名先打起来，最后甩一句"Tell me I'm wrong"勾火。品牌只在最后才落地："MODAY — Wear the day you survived."

整条片子，**产品的硬卖被藏在最后两秒**。视频本身不像广告，是当 meme 在被消费，评论区帮你干活。拉客策略本来就是我顾问本职的领域，结果这次我整个甩给了 AI。

而且 AI 出来的方案，明显比我自己写的要靠谱。

## 第三步：用 ChatGPT Image 起四个能反复用的模特

要做系列短视频，**得有能反复出场的角色**。真人模特我请不起，拍摄的时间也没有。我让 ChatGPT Image 2.0 一次性出了四个模特。

![Model 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Model 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Model 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Model 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

族裔、年龄、性别我都拉开了。工程师感、远程办公者感、上班族感这条主线留住，四个人各自的气质都不一样。

每个模特正面、四十五度、侧脸、几种表情，一次 prompt 全出齐。这就是我视频系列里的常驻演员。**四个属于这个品牌的"专属模特"。**

租摄影棚、找模特经纪公司、备服装、布灯光——全跳过。成本几乎是零。总耗时大概三十分钟。

## 从这里往后，得自己动手

接下来的步骤是这样：

1. 把每个场景合成静态图（模特 + 穿上 T 恤 + 背景）。
2. 把静态图动起来，做成视频。
3. 加音效和字幕。
4. 发到 TikTok / Instagram Reels / YouTube Shorts。

这一轮，**多语言铺开和自动化我都先往后推**。先用英语做一条，纯手工做出来，扔出去看看。打中了，再把这套打法横向拉到九种语言，去搭背后的自动化管线。没打中，就换个角度再试。

这套逻辑，其实就是 Web 开发里那一招——**先手搓一个能跑的原型，看清赢的样子之后再砸钱上自动化。** 拉客这事一样适用。

## 嘴上说 AI 驱动，可还是有得回手做的时候

上一篇里我说过——"能甩给 AI 的全甩出去"。这条原则我没改。这一轮，分镜、模特、策略，全是 AI 出的。

但是**第一条视频的合成和剪辑，我打算亲自动手**。不是因为技术上 AI 做不了，是因为——**第一条的手感，我得亲自摸一遍**。

哪一帧抓住了观众，他们在哪一秒划走，评论区会演成什么样。这些东西我不亲眼看一遍，进到自动化阶段就没有判断尺度。手搓一条，命中也好，扑街也好，把这段经验记下来——这才是后面要用的**判断标准的原材料**。

品牌是 AI 驱动没错，但**判断权一直在我手里**。什么时候交出去、什么时候不交，这条边界是创始人的活。而现在，就是那种"得自己上手"的时刻。

顺便贴一下，这是做出来的第一条：

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

第一条能不能爆我现在还说不准。爆了就进自动化，扑了就换角度。不管哪种结果，一个新的回路都会从这里开始转。

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
