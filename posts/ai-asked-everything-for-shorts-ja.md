<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# ショート動画を作るために、知らないことを全部AIに聞いた

## 「観測のループ」の話を、撤回する

別の記事で「観測のループが回り始めた」と書いた。
ストアを開けた瞬間から、世界が返事をくれる時間に変わった、と。

公開して4〜5日経って、分かったことがある。
**観測する母数が、足りない**。

GA4 を眺めても、カート行動を追っても、チャットbot のログを覗いても、
サンプルが少なすぎて何も言えない。
仮説を立てるには、まずもう少し人が来ないと話にならない。

観測より先に、**母数を増やすこと**が要る。
順番を間違えていた。

## 一回ちゃんと、集客のために手を動かす

ここまでの構築フェーズは、ひたすら **仕組みを作る** ことに振っていた。
9言語10媒体配信、チャットbot 自動化、注文→生産の自動化、改善ループの自動化。
全部「仕組みを作って、あとは流す」の発想。

集客も、本当は同じ発想でやりたかった。
広告予算でブースト → データが集まる → AI が改善案を出す → 自動化、というループ。

でも、別の記事で書いた通り、いまは広告予算が組めない。
広告が無いなら、**SNS で当てに行くしかない**。
特にショート動画。商品の性質的にも、視覚的に一発で伝わるフォーマットがハマるはず。

ただ、ひとつ問題があった。
**自分は、ショート動画で何が流行ってるか、全く分からない**。

日本語のショート動画も、追いかけて見ているわけじゃない。
英語圏のショート動画に至っては、輪をかけて知らない。
ECコンサルを本職にしていて、これは弱点として晒すしかない。
強みじゃないところに踏み出している、という自覚はある。

## まず Gemini に聞いた

Google I/O のニュースを眺めていたタイミングで、ちょうど Gemini を試したかった。
「英語圏のビジネスマン向けに、いま TikTok / LinkedIn / Shorts で流行っている動画の傾向は?」
そんな質問を投げた。

返ってきたのが、自分にとってほぼ完全に未知の世界。

- **Corporate Buzzword Satire**：「Synergy」「Circle back」「Let's take this offline」みたいな、中身のないビジネス用語を皮肉るコント
- **"Day in the Life" の自虐版**：「ベッドから出ずに Teams を Active にする方法」みたいな、企業の歯車感を笑う動画
- **Corporate Erin 系**：冷酷な人事を演じるキャラ。プロフェッショナルな笑顔と早口で、レイオフ通達を包み込むモノマネ
- **LinkedIn Lunatics**：ポエム化したビジネス投稿を、TikTok で音読してイジる

Gemini が拾った共通項が、刺さった。
英語圏のビジネス系バズの本質は、**「理不尽な企業文化への、ユーモアを使った反逆」**。

これは MODAY と、文化的に完全に地続きの領域だった。
「MONDAY: System Booting...」「FRIDAY: Build Successful ✓」というTシャツの世界観は、
このカルチャーの中にある。

自分の頭だけで考えていたら、絶対この4つには辿り着けなかった。

## Codex に絵コンテを描かせた

Gemini で得た情報を、そのまま Codex に渡した。
「MODAY の集客用ショート動画のシナリオを、22秒の縦型 9:16 で書いて。
英語圏のビジネスマン向け、皮肉とユーモアで、最後にブランド着地」。

返ってきたのが、これ。

![Storyboard: Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

「**Weekdays Ranked by Developer Damage**」。
曜日を、開発者をどれだけ壊すかでランキングする、というコンセプト。
Tシャツの商品紹介ではなく、**ミーム動画として完結する** 構造。
コメント欄で順位を巡って議論が起きる前提で、最後に「Tell me I'm wrong」で煽る。
そこで初めて、ブランド名「MODAY」と「Wear the day you survived.」が出る。

これ、商品の紹介を **最後の2秒に隠した** 設計になっている。
動画として広告に見えない、ミームとして消費される、コメント欄で議論される。
集客の戦略を考えるのは、コンサルとしての本職領域だが、それを今回は完全に AI に丸投げした。

しかも自分が組むより、明らかに筋がいい。

## ChatGPT Image でモデルを4人作った

動画シリーズに必要なのは、**継続して使えるモデル**。
実写の人を雇うコストも、撮影の手間も、今は持っていない。
ChatGPT Image 2.0 で、4人分のモデルを一括生成した。

![Model 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Model 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Model 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Model 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

民族、年齢、性別をばらけさせた。
エンジニアらしさ、リモートワーカーらしさ、ビジネスマンらしさ、
というトーンを残したまま、4人とも別の雰囲気を持たせている。

各モデル、正面・斜め・横顔・複数の表情まで、1回のプロンプトで揃った。
これを今後の動画で使い回す。**4人分の、自分のブランド専属モデル**。

撮影スタジオを借りる、モデル事務所を当たる、衣装を仕込む、ライティングを組む。
全部スキップした。コストはほぼゼロ。所要時間はトータルで30分くらい。

## ここから先は、手動でやる

ここから先のステップは、こう。

1. 各シーンを、静止画で合成する（Tシャツを着せた状態のモデル + 背景）
2. その静止画を、動画化する
3. SE と字幕を載せる
4. TikTok / Instagram Reels / YouTube Shorts に投稿する

今回は、**多言語展開も、自動化も、次のステップ** に置いた。
まず英語1本で、手動で作って、当てに行く。
当たれば、その勝ち筋を多言語にスケールさせる。自動化のパイプラインを組む。
外れれば、別の角度を試す。

これは Web 開発の世界でよくある作法で、
「**まず手で動くプロトタイプを1個作って、勝ち筋が見えたら自動化に投資する**」
というやつ。集客でも同じ。

## AI 駆動型と言いつつ、手動に戻る瞬間がある

別の記事で「なるべく全部 AI に渡す」と書いた。
方針は変えていない。今回も、絵コンテも、モデルも、戦略立案も、AI が組んだ。

ただ、**動画の合成と編集だけは、自分の手でやる**。
ここを手動にしたのは、技術的に AI でやれないからじゃない。
**1本目の感触を、自分の手で掴みたい** から。

何が刺さるか、どこで観客が離脱するか、コメント欄で何が起きるか。
これを自分の手で観測しないと、自動化フェーズに渡す判断軸が作れない。
手で作って、当てて、外して、その経験を **判断軸の材料にする**。

AI 駆動型のブランドだが、**判断軸はずっと自分が持つ**。
渡すタイミングと、渡さないタイミング、その境界線を引くのは自分。
そして今は、手を動かすタイミングだった。

ちなみに、できあがった1本目はこれ。

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

1本目が当たるか外れるかは、まだ分からない。
当たれば自動化、外れれば別の角度。
どちらにしても、ここから新しいループが始まる。

それでは、また書きます。

— Yoskee  
[moday.me](https://moday.me)

---

<!-- moday-product-card -->
### 今日を着る。— MODAY のTシャツを手に入れる

| セット | 枚数 | 価格 |
|---|---|---|
| **[一週間セット →](https://moday.me/collections/bundle-full-week)** | Mon–Sun (7) | $159 |
| **[平日セット →](https://moday.me/collections/bundle-workweek)** | Mon–Fri (5) | $119 |
| **[スターターパック →](https://moday.me/collections/bundle-starter)** | Mon · Wed · Fri (3) | $79 |
| **[週末セット →](https://moday.me/collections/bundle-weekend)** | Sat · Sun (2) | $55 |

*$99以上で送料無料 · 8色 × 6サイズ · 9言語*
