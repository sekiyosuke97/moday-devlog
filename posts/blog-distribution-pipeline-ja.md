<!-- canonical: https://moday.me/blogs/engineering/blog-distribution-pipeline -->

# MODAY構築ブログを9言語10媒体に配信するパイプライン

## JA 原本1本書くと、9言語10媒体に届く

MODAY の構築ブログは、日本語の原稿を1本書くと、こういう場所に配信される。

| 種別 | プラットフォーム |
|---|---|
| 自社 | Shopify Blog（JA + 8ロケール）|
| 自動配信 | dev.to / Qiita / Zenn / GitHub devlog |
| 手動配信 | note / Medium / Tumblr |

書く側がやる作業は、原稿を書いて、`distribute.py` を1回叩くだけ。
あとは勝手に広がっていく。

このパイプラインを、3日で組んで、第1記事から使っている。
中身をそのまま書きます。

## 設計の考え方 — 「自動配信」と「手動配信」を分ける

最初に方針として置いたのは、**配信先を2層に分ける** こと。

API があって自動投稿できる媒体（Shopify / dev.to / Qiita / Zenn / GitHub）と、
API が無い・制限がきつい媒体（note / Medium / Tumblr）。
この2つを混ぜると、スクリプトが複雑になる。

なので、
- 自動配信は `distribute.py` が API で全部やる
- 手動配信は `prepare_handoff.py` が **貼り付け用のファイル** を吐く

という分担にした。
手動配信先には、最終的には人間（自分）がブラウザで貼り付けに行く。
ここは AI に渡せていない領域だけど、貼り付けの直前までは自動化されている。

## distribute.py の仕事

`distribute.py` がやっているのは、こんな流れ。

1. **起動時チェック（hero gate）**: `content/posts/<slug>/hero.png` が無いと、即停止する。アイキャッチ画像なしでは配信させない、というガード
2. **Shopify Journal に投稿**: 本文と hero 画像を一緒に POST
3. **Shopify 翻訳登録**: 隣接ファイル `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` を読み、`translationsRegister` API で8ロケール一括登録
4. **dev.to に POST**: EN 版を本文として送る。cover には Shopify の CDN URL を流用
5. **Qiita に POST**: JA 原本＋canonical link で送る
6. **Zenn**: API は使わない。GitHub に push したものを、Zenn 側が自動取り込みする設定にしてある
7. **GitHub devlog**: `moday-devlog` repo に `<slug>-ja.md` / `<slug>-en.md` / `<slug>-hero.png` を commit
8. **prepare_handoff.py を呼び出す**: 手動配信先（note / Medium / Tumblr）用のファイルをここで生成
9. **status.json に記録**: 各媒体の URL / ID / 投稿日を JSON で残す

特に気に入っているのが、**hero gate** と **Zenn の GitHub 経由ルート**。
hero gate は、アイキャッチ忘れによる配信事故を構造的に防ぐ。
Zenn は API 投稿に対応していないが、GitHub 連携機能があるので、
そこを使えば結果的に「push 1発で Zenn にも記事が立つ」状態が作れる。

## prepare_handoff.py の仕事

手動配信先（note / Medium / Tumblr）のために、貼り付け用のファイルを吐く。

| ファイル | 内容 | 言語 |
|---|---|---|
| `note.md` | JA 原本に paste 手順コメント付き。表は note でレンダされないので「見出し: 値」形式に自動変換 | JA |
| `medium.html` | EN 翻訳を HTML 化。操作手順バナー（コピー不可CSS）＋本文。⌘+A → ⌘+C で本文だけコピーできる構造 | EN |
| `tumblr.md` | EN 本文の lede（H1〜最初のH2まで、1500字キャップ）＋canonical link＋Tumblr用タグ一覧 | EN |

ここで一番重要なのは、**プラットフォームの方言に合わせる** こと。

note は Markdown テーブルがレンダリングされない。
そのまま投稿すると、表が「| 見出し | 値 |」の生テキストで表示されて、悲惨な見た目になる。
だから `prepare_handoff.py` の中で、テーブルを「**見出し: 値**」形式の段落に
自動変換している。

Medium は逆に、コピーするときに不要なメタ情報まで持っていかれやすい。
なので、操作手順をバナーで上に出しつつ、**バナー部分はコピー対象から除外する CSS** を仕込んだ HTML を出力している。
ブラウザで開いて ⌘+A → ⌘+C すれば、本文だけがクリップボードに入る。

Tumblr は文化として「全文を貼る」のはあまり合わないので、
リード部分（最初のH2まで）だけを抜粋して、本文は canonical に誘導する。

各プラットフォームの **方言と文化** に合わせた変換を、ここでまとめてやっている。

## 翻訳も AI に渡している、ただし「サブスクの中で」

「AI駆動型ブランド立ち上げ」を掲げている以上、翻訳も当然 AI にやらせる。
ただし、やらせ方を最近変えた。

- 旧版：`distribute.py` の中で Anthropic API（Claude Haiku）を叩いて自動翻訳
- 新版：Claude Code（Opus 4.7）に直接「8ロケール rewrite して」と頼む

理由は単純で、**API 課金を別に払いたくない** から。
Claude Max を契約していて、月のサブスク料は払っている。
だったらその中でやれることはその中でやってほしい。

これは技術判断というより **経営判断** の話。
スタートアップで一番大事なのは固定費を抑えることで、
「Anthropic API の従量課金」と「Claude Max のサブスク」が二重に走るのは、
個人事業としては筋が悪い。

それともう一つ大事なのが、**翻訳の質**。
Haiku で API 経由で叩いていた頃は、出てきたものが直訳寄りだった。
9言語に展開する以上、**各言語ネイティブの founder が書いたレベル** まで
書き直さないと、ブランドとして刺さらない。

これは翻訳じゃなくて **ローカライズ・リライト** と呼ぶべき作業で、
Opus 4.7 を Claude Code 経由で使うほうが、出力の質が上がった。

コストを下げたら、結果的に質も上がった。
これは予想外の副産物だった。

## 典型的な配信フロー

実際のオペレーションはこうなっている。

1. モバイル Claude で JA 原稿を下書き
2. Claude Code セッションで `webhook/posts/004-<slug>-ja.md` として配置
3. Claude Code に「8ロケール rewrite して」と頼む → `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` が生成される
4. `webhook/generate_hero.py` でアイキャッチ生成 → `content/posts/<slug>/hero.png`
5. `python webhook/distribute.py webhook/posts/004-<slug>-ja.md`
   → Shopify(JA+8ロケール) / dev.to / Qiita / GitHub に自動配信
   → 末尾で `prepare_handoff.py` が `content/posts/<slug>/{note.md, medium.html, tumblr.md}` を吐く
6. note / Medium / Tumblr の UI を開いて、生成済みファイルを貼り付け

このフローの中で、自分が **頭を使う** のは1ステップ目だけ。
それ以外は、Claude Code への指示と、`distribute.py` の実行と、貼り付けだけ。

## 通勤中にネタ → 帰宅後に配信、までを1日で

このパイプラインで一番気に入っているのが、**人間側のフロー** のほう。

ネタを思いつくのは、たいてい通勤中とか、寝る前とか、机から離れているとき。
そういうときに、スマホの Claude アプリでこの Project を開いて、壁打ちする。
1記事分の原稿が、移動時間でほぼ出来上がる。

帰宅したら、Claude Code セッションを立ち上げて、原稿を渡す。
あとは Claude Code が rewrite して、`distribute.py` を叩いて、配信が走る。

「ネタを思いつく」と「配信が走る」の間に、**自分が机に座って黙々と作業する時間が、ほぼゼロ** 。
これが、AI 駆動型ブランド立ち上げの実態として、いま一番手応えがあるところ。

## 結び

このパイプライン自体も、Claude Code が書いた。
僕は「9言語10媒体に配信するスクリプトが欲しい」と言って、
細かい仕様を会話で詰めていっただけ。

今後やりたいことは、まだいくつかある。
Tumblr の API 化、status.json のダッシュボード化、SNS への自動展開。
このあたりは、また走りながら組み込んでいくつもり。

それでは、また書きます。

— Yoskee  
[moday.me](https://moday.me)
