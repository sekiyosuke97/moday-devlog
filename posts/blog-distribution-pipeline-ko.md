<!-- canonical: https://moday.me/blogs/engineering/blog-distribution-pipeline -->

# 한 번 쓰면 9개 언어, 10개 매체로 — MODAY 배포 파이프라인

## 일본어 원고 한 편을 쓰면, 9개 언어 10개 매체로 흘러간다

MODAY의 개발 일지(devlog)는 일본어로 한 편을 끝내면, 이런 곳으로 퍼져나간다.

| 구분 | 매체 |
|---|---|
| 자체 매체 | Shopify Blog (JA + 8개 로케일) |
| API 자동 배포 | dev.to / Qiita / Zenn / GitHub devlog |
| 수동 붙여넣기 (핸드오프 파일 생성) | note / Medium / Tumblr |

글쓰는 쪽이 하는 일은 딱 두 가지다. 원고를 마무리한다. `distribute.py`를 한 번 실행한다. 나머지는 알아서 퍼진다.

이 파이프라인을 3일 만에 만들었고, 1번째 글부터 전부 이걸로 돌리고 있다. 실제 구조를 그대로 적어둔다.

## 설계 방침 — "자동"과 "수동"을 처음부터 갈라둔다

가장 먼저 정한 것은 **배포 대상을 두 계층으로 나누는 것**이었다.

쓰기 API가 제대로 동작하는 매체 (Shopify, dev.to, Qiita, Zenn-via-GitHub, GitHub 자체) 한쪽. API가 아예 없거나, 있어도 까칠한 매체 (note, Medium, Tumblr) 다른 한쪽. 이걸 한 스크립트로 묶으려고 시도하는 순간, 코드는 늪이 된다.

그래서 이렇게 갈랐다.

- 자동 계층 — `distribute.py`가 HTTP로 전부 처리한다
- 수동 계층 — `prepare_handoff.py`가 **붙여넣기 전용 파일**을 떨궈주면, 인간이 그걸 들고 UI로 간다

수동 계층은 아직 AI에게 넘기지 못한 부분이다. 다만 붙여넣기 직전까지의 모든 공정은 자동화되어 있다.

## `distribute.py`가 실제로 하는 일

내부 흐름은 이렇다.

1. **시작 시점에 hero gate를 건다**. `content/posts/<slug>/hero.png`가 없으면 스크립트가 즉시 멈춘다. 커버 이미지 없으면 배포 안 한다는 뜻이다. "아, 히어로 이미지 또 까먹었네" 같은 사고를 구조적으로 막는 가드다.
2. **Shopify Journal 블로그에 발행한다**. 본문과 히어로 이미지를 한 번에 POST한다.
3. **Shopify 번역을 등록한다**. 이웃 파일 `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`을 읽어서 8개 로케일을 `translationsRegister` API로 한 방에 집어넣는다.
4. **dev.to에 POST한다**. 본문은 EN 버전, cover는 Shopify CDN URL을 재활용한다.
5. **Qiita에 POST한다**. 본문은 JA 원본, `canonical_url`은 Shopify 쪽을 가리키게 한다.
6. **Zenn — API 호출은 없다**. Zenn은 쓰기 API를 일부러 공개하지 않기 때문에, Zenn ↔ GitHub 연동을 미리 설정해뒀다. push 한 번이면 글이 알아서 올라온다.
7. **GitHub devlog**: `moday-devlog` 리포지토리에 `<slug>-ja.md`, `<slug>-en.md`, `<slug>-hero.png`를 commit한다.
8. **`prepare_handoff.py`를 호출한다**. 수동 계층 매체용 붙여넣기 파일을 여기서 만든다.
9. **`status.json`을 원고 옆에 쓴다**. 각 매체별로 URL / ID / 발행 시각을 JSON으로 남긴다.

가장 마음에 드는 두 가지는 **hero gate**와 **Zenn을 GitHub 경로로 우회하는 것**이다. hero gate는 커버 없이 발행되는 사고를 구조적으로 불가능하게 만든다. Zenn은 의도적으로 쓰기 API를 막아둔 매체인데도, `git push` 하나가 다리 역할을 해주니까 결과적으로 글이 올라간다.

## `prepare_handoff.py`가 하는 일

수동 계층 세 군데를 위한 붙여넣기 전용 파일을 떨군다.

| 파일 | 내용 | 언어 |
|---|---|---|
| `note.md` | JA 원본 + 붙여넣기 절차 주석. note는 Markdown 테이블을 렌더링하지 못해서, 표는 "**라벨:** 값" 단락으로 자동 변환된다 | JA |
| `medium.html` | EN 번역의 HTML 버전. 상단에 안내 배너 (복사 불가 CSS), 본문은 그 아래. ⌘+A → ⌘+C 하면 본문만 클립보드에 들어온다 | EN |
| `tumblr.md` | EN 리드 부분 (H1부터 첫 번째 H2까지, 1500자 하드캡) + canonical 링크 + Tumblr식 태그 블록 | EN |

여기서 안 보이지만 중요한 핵심은 **매체별 방언**이다.

note는 Markdown 테이블을 안 그려준다. 원본을 그대로 붙이면 `| 헤더 | 값 |`이 텍스트로 표시되는 참사가 벌어진다. 그래서 `prepare_handoff.py` 안에서 모든 표를 굵은 라벨 단락으로 다시 짠다.

Medium은 반대 문제다. 아무 데서나 복사해서 붙이면 메타데이터까지 같이 따라오기 십상이다. 그래서 글쓴이(나)가 페이지를 ⌘+A → ⌘+C 했을 때 *본문만* 깔끔하게 들어오게 만들고 싶었다. 그래서 출력 HTML은 상단에 `user-select: none` CSS가 걸린 안내 배너를 띄운다. 눈에는 보이지만, 클립보드에는 안 들어간다.

Tumblr 문화는 3,000자짜리 에세이를 통째로 던지는 걸 별로 좋아하지 않는다. 그래서 리드만 발췌하고, 본문은 canonical로 유도한다.

각 플랫폼의 **방언과 문화**를 한 곳에서 챙긴다. 그게 이 파일의 존재 이유다.

## 번역도 AI에게 맡긴다 — 단, 구독 안에서만

MODAY 자체가 "AI 주도형 브랜드 빌드"를 표방하니까, 번역도 당연히 AI에게 던진다. 다만 던지는 방식을 최근에 바꿨다.

- 이전: `distribute.py`가 로케일마다 Anthropic API의 Claude Haiku를 호출했다.
- 지금: Claude Code (Opus 4.7)에게 세션 안에서 직접 "8개 로케일로 다시 써줘"라고 부탁한다.

이유는 시시하다. **두 번째 종량제 청구서를 만들고 싶지 않다.** Claude Max를 이미 구독하고 있다. 그 안에서 끝낼 수 있는 일은 그 안에서 끝내야 한다.

이건 기술적 판단이라기보다 **경영 판단**에 가깝다. 1인 운영 가게에서 가장 중요한 건 고정비를 누르는 일이다. 같은 작업에 Claude Max 구독료와 Anthropic API 종량 과금이 동시에 흐른다면, 그건 그냥 개인 PL 운영이 허술하다는 뜻이다.

또 하나 컸던 건 **품질**이다. Haiku-API 시절의 결과물은 딱 "번역체"였다. 쓸 수는 있지만 네이티브의 글은 아니었다. 9개 로케일로 펼친다는 건, 각 시장의 현지 founder가 본인 블로그에 쓴 글처럼 읽혀야 한다는 뜻이다. 그게 안 되면, 어느 시장에서도 브랜드가 안 박힌다.

이건 번역이 아니라 **로컬라이즈-리라이트**라고 불러야 맞는 작업이고, Claude Code 위에서 Opus 4.7로 돌리니까 이전 Haiku-API 라인보다 결과물이 눈에 띄게 좋아졌다.

비용을 깎았더니, 품질이 같이 올라갔다. 이건 예상 못 했던 부수입이다.

## 실제 일과는 이렇게 돌아간다

운영 리듬은 지금 이렇다.

1. 모바일 Claude로 JA 초고를 쓴다 (대개 출퇴근길 지하철에서).
2. Claude Code 세션을 열어서 `webhook/posts/004-<slug>-ja.md`에 놓는다.
3. Claude Code에게 "8개 로케일로 리라이트해줘"라고 부탁한다 → `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`이 생성된다.
4. `webhook/generate_hero.py`로 히어로 이미지를 만든다 → `content/posts/<slug>/hero.png`.
5. `python webhook/distribute.py webhook/posts/004-<slug>-ja.md`.
   - Shopify (JA + 8개 로케일), dev.to, Qiita, GitHub로 자동 배포.
   - 마지막에 `prepare_handoff.py`가 `content/posts/<slug>/{note.md, medium.html, tumblr.md}`를 떨군다.
6. note / Medium / Tumblr UI를 열어서 준비된 파일을 붙여넣는다.

내가 *머리를 굴리는* 단계는 1번뿐이다. 나머지는 Claude Code에게 지시 한 줄, 스크립트 실행 한 번, 그리고 붙여넣기다.

## "지하철에서 떠올랐다"에서 "전부 라이브 됐다"까지, 하루 안에

이 파이프라인에서 가장 좋아하는 건 사실 스크립트가 아니라 **사람 쪽 흐름**이다.

아이디어는 책상 앞에서 안 떠오른다. 통근길. 자기 직전. 걸어가다가. 그럴 때 모바일 Claude를 열어서, MODAY 프로젝트를 띄우고, 글에 대해 떠든다. 집에 도착할 즈음이면 초고는 거의 완성돼 있다.

책상에 앉으면 Claude Code를 열고, 초고를 건네고, 로케일 리라이트가 나오고, 파이프라인이 돈다.

내가 *책상 앞에 앉아 묵묵히 글자를 밀고 있는* 시간이 거의 0에 가깝다. "AI 주도형 브랜드 빌드"라는 말이 지금 가장 실감 나는 지점이 바로 이 부분이다.

## 마무리

이 파이프라인 자체도 Claude Code가 썼다. 나는 "9개 언어 10개 매체에 배포하는 스크립트를 갖고 싶다"고 한 줄 던지고, 세부 사양은 대화하면서 조율한 것뿐이다.

아직 to-do에 남은 것들이 있다. Tumblr API화, `status.json` 대시보드, SNS로의 자동 fan-out. 이런 건 브랜드가 계속 굴러가는 동안 하나씩 끼워 넣을 생각이다.

또 쓰러 올게요.

— Yoskee  
[moday.me](https://moday.me)

---

<!-- moday-product-card -->
### 오늘을 입다. — MODAY 티셔츠

| 세트 | 장수 | 가격 |
|---|---|---|
| **[풀 위크 세트 →](https://moday.me/collections/bundle-full-week)** | Mon–Sun (7) | $159 |
| **[워크위크 세트 →](https://moday.me/collections/bundle-workweek)** | Mon–Fri (5) | $119 |
| **[스타터 팩 →](https://moday.me/collections/bundle-starter)** | Mon · Wed · Fri (3) | $79 |
| **[위켄드 세트 →](https://moday.me/collections/bundle-weekend)** | Sat · Sun (2) | $55 |

*$99 이상 무료 배송 · 8색 × 6사이즈 · 9개 언어*
