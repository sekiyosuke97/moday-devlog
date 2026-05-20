<!-- canonical: https://moday.me/blogs/engineering/blog-distribution-pipeline -->

# 一篇日文稿，九种语言十个平台：MODAY 的分发流水线

## 一篇日文原稿，落到 9 种语言 10 个地方

MODAY 的构建日志，写作侧的动作只有一件事：写一篇日文稿，然后这篇稿子会自己出现在下面这些地方。

| 类型 | 平台 |
|---|---|
| 自家阵地 | Shopify Blog（JA + 8 个语言版本）|
| API 自动分发 | dev.to / Qiita / Zenn / GitHub devlog |
| 手动粘贴（带 handoff 文件）| note / Medium / Tumblr |

写的人要做的，就是把稿子写完，然后敲一次 `distribute.py`。剩下的事情，它自己会扩散出去。

这套流水线我用三天搭出来，从第 1 篇开始就一直在用。下面把它整个掰开讲一下。

## 设计上的第一刀——把"自动"和"手动"拆开

最早定下来的规则是：**把目标平台分成两层**。

一层是有可用写入 API 的（Shopify、dev.to、Qiita、Zenn-via-GitHub、GitHub 本体）。另一层是没有 API 或者 API 形同虚设的（note、Medium、Tumblr）。一旦想用一份代码把这两类统一掉，脚本立马变成一坨。

所以分工是这样的：

- 自动层：`distribute.py` 用 HTTP 把所有事情做完
- 手动层：`prepare_handoff.py` 吐出 **可以直接粘贴的文件**，由人（也就是我）拿到浏览器里去贴

手动层是我目前还没法完全交给 AI 的那一块。但**贴的前一秒之前**，全程都是自动的。

## `distribute.py` 到底干了什么

里面的流程大致是这样：

1. **启动时的 hero gate**：如果 `content/posts/<slug>/hero.png` 不存在，脚本直接终止。**没有封面图，就不允许分发。** 这是一道结构性的保险，防止"啊我忘了配封面"这种事故
2. **发到 Shopify Journal**：正文加 hero 一起 POST
3. **登记 Shopify 翻译**：读 `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` 这一组同名文件，通过 `translationsRegister` API 把 8 个 locale 一次性灌进去
4. **发到 dev.to**：用 EN 版作为正文，封面图复用 Shopify 的 CDN URL
5. **发到 Qiita**：用 JA 原稿，配 `canonical_url` 指回 Shopify
6. **Zenn——不调 API**：Zenn 故意不开放写入 API，所以我配的是 Zenn 与 GitHub 的双向同步。`git push` 一推，文章自动就立起来了
7. **GitHub devlog**：把 `<slug>-ja.md` / `<slug>-en.md` / `<slug>-hero.png` commit 到 `moday-devlog` 这个 repo
8. **调用 `prepare_handoff.py`**：生成手动层（note / Medium / Tumblr）用的粘贴文件
9. **写 `status.json`**：把每个平台的 URL / ID / 投稿时间记到原稿旁边的 JSON 里

我自己最满意的两块是 **hero gate** 和 **Zenn 走 GitHub 这条桥**。hero gate 让"忘配封面就上线"这种事在结构上做不到。Zenn 虽然不给 API，但通过 GitHub 同步绕过去之后，**等于一次 push 就把 Zenn 的稿子也立起来了**。

## `prepare_handoff.py` 在干嘛

它的工作是为三个手动平台各吐出一份可以直接粘贴的文件：

| 文件 | 内容 | 语言 |
|---|---|---|
| `note.md` | JA 原文加粘贴说明注释。因为 note 不渲染 Markdown 表格，表格会被自动转成"**字段：值**"形式的段落 | JA |
| `medium.html` | EN 翻译转 HTML。顶部带操作说明 banner（CSS 禁选），下面是正文。⌘+A → ⌘+C 只会复制到正文 | EN |
| `tumblr.md` | EN 的开头部分（H1 到第一个 H2，硬上限 1500 字符）+ canonical link + Tumblr 风格的 tag 块 | EN |

这里真正不那么显然的，是 **每个平台的方言要单独适配**。

note 不渲染 Markdown 表格——你要是直接把原稿贴进去，表格会以 `| 字段 | 值 |` 这种字面文本的形式显示出来，画面非常惨。所以 `prepare_handoff.py` 会把每一个表格在写出去之前重写成"加粗字段名 + 段落"的形态。

Medium 是相反的问题：从任何地方复制粘贴过来，都很容易把多余的 metadata 一起拖进去。我希望写稿人（也就是我）能在浏览器里直接 ⌘+A → ⌘+C，**剪贴板里只剩正文**。所以输出的 HTML 顶部带一个操作说明 banner，用 `user-select: none` 标住——人看得见，剪贴板看不见。

Tumblr 的文化也不奖励你往里塞一篇三千字的长文。所以我只摘开头那段，正文链回 canonical。

每个平台的 **方言和文化**，都在这一个地方统一适配掉。

## 翻译也交给 AI——但是要"在订阅之内"

MODAY 整个就是奔着"AI 驱动的品牌搭建"去做的，所以翻译当然也交给 AI。但具体怎么交，我最近换了一种做法。

- 旧版：`distribute.py` 在内部去调 Anthropic API（Claude Haiku）做翻译
- 新版：在 Claude Code（Opus 4.7）里直接说"帮我重写到 8 个 locale"

理由很俗：**我不想再为它付第二份按量计费的账单**。我已经在订阅 Claude Max。能在订阅内完成的事，就在订阅内完成。

这一刀与其说是技术判断，不如说是 **经营判断**。对一个一人公司来说，最重要的事就是把固定支出控住。"Claude Max 订阅"和"Anthropic API 按量计费"同时为同一件事跑账，这在个人 P&L 上是个不漂亮的姿势。

另一件同样关键的事是 **质量**。当初走 Haiku-API 那条路的时候，产出读起来就是"翻译稿"——能用，但不像本地人写的。9 种语言要往外铺，必须做到 **像本地的 founder 在当地亲手写出来一样**。做不到这个，品牌在那个市场就立不住。

这种活儿其实已经不是"翻译"了，叫 **本地化重写** 更贴切。用 Claude Code 的 Opus 4.7 跑出来，比之前 Haiku-API 那条路的产出明显高一档。

把成本降下来，结果质量反而上去了。这是意料之外的副产物。

## 实际的日常节奏

现在这套东西在我手里跑起来，节奏大致是这样：

1. 在手机的 Claude App 里起一篇 JA 草稿（一般是在地铁上）
2. 回到 Claude Code session 里，把它落到 `webhook/posts/004-<slug>-ja.md`
3. 让 Claude Code "帮我重写到 8 个 locale"——它会产出 `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`
4. 用 `webhook/generate_hero.py` 生成封面图 → `content/posts/<slug>/hero.png`
5. 跑 `python webhook/distribute.py webhook/posts/004-<slug>-ja.md`
   - 自动分发到 Shopify（JA + 8 个 locale）/ dev.to / Qiita / GitHub
   - 末尾顺手调 `prepare_handoff.py`，吐出 `content/posts/<slug>/{note.md, medium.html, tumblr.md}`
6. 打开 note / Medium / Tumblr 的网页，把生成好的文件贴进去

整个流程里，我 **真正用脑子** 的只有第 1 步。剩下的就是对 Claude Code 下指令、跑一次脚本、再做几次粘贴。

## "在路上想到选题"到"全网上线"，一天搞定

这套东西我最喜欢的部分其实不是脚本——是 **人那一侧的节奏**。

选题这种东西，一般都是我离开桌子的时候蹦出来的。通勤路上、睡前、走路去吃饭。这种时候我就打开手机的 Claude，把 MODAY 这个 Project 拉出来，对着它把这篇文章过一遍。到家的时候，初稿基本上已经成形了。

回到桌前打开 Claude Code，把稿子丢过去，它出 8 个 locale 的重写版本，再跑一次流水线。

**我坐在桌前一个字一个字往外推的时间，几乎为零。** "AI 驱动的品牌搭建"这件事现在最让我觉得"真的在发生"的，就是这一段。

## 收尾

这套流水线本身，也是 Claude Code 写的。我只说了一句"我要一个能把稿子分发到 9 种语言 10 个平台的脚本"，剩下的细节是我们一边聊一边敲出来的。

待办清单还剩几项：Tumblr 的 API 化、`status.json` 的 dashboard、向社交媒体的自动扩散。等品牌再往前走一段，我会顺手把这些补进去。

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
