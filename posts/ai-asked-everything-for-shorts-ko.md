<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# 숏폼을 만들기 위해, 모르는 걸 전부 AI한테 물어봤다

## "관측 루프" 얘기, 일단 철회한다

지난 글에서 "관측 루프가 돌기 시작했다"라고 썼다. 스토어를 연 순간부터 세상이 답을 주는 시간이 시작됐다고.

오픈하고 4~5일 지나서, 알게 된 게 있다.
**관측할 모수가, 너무 부족하다.**

GA4를 들여다봐도, 카트 행동을 따라가도, 챗봇 로그를 열어봐도, 샘플이 너무 적어서 아무 말도 못 한다. 가설을 세우려면, 일단 사람이 좀 더 와줘야 얘기가 된다.

관측보다 먼저, **모수를 늘리는 일**이 필요했다. 순서를 잘못 잡았다.

## 한 번 제대로, 집객을 위해 손을 움직인다

여기까지의 구축 단계는, 오로지 **시스템을 짜는 일**에 다 쏟았다. 9개 언어 10개 매체 배포, 챗봇 자동화, 주문→생산 자동화, 개선 루프 자동화. 전부 "시스템 만들고 나면 그냥 흘려보낸다"는 발상.

집객도, 사실은 같은 발상으로 가고 싶었다. 광고 예산으로 부스트 → 데이터 쌓이고 → AI가 개선안 뽑고 → 자동화, 이 루프.

근데 다른 글에서도 썼지만, 지금 광고 예산은 못 쓴다. 광고가 없으면 **SNS에서 승부 보는 수밖에 없다**. 특히 숏폼. 제품 성격상으로도, 시각적으로 한 방에 꽂히는 포맷이 맞아떨어질 것 같다.

근데 한 가지 문제가 있었다.
**나는, 숏폼에서 뭐가 유행하는지 전혀 모른다.**

한국어 숏폼도, 막 챙겨 보는 편이 아니다. 영어권 숏폼은 더더욱 모른다. 본업이 EC 컨설팅인데, 이건 약점으로 그냥 인정하는 수밖에 없다. 강점이 아닌 영역으로 발을 내딛고 있다는, 그 자각은 있다.

## 우선 Gemini한테 물어봤다

Google I/O 뉴스를 훑어보던 타이밍이라, 마침 Gemini를 한번 굴려보고 싶었다. "영어권 비즈니스맨 대상으로, 지금 TikTok / LinkedIn / Shorts에서 유행하는 영상의 경향은?" 이런 질문을 던졌다.

돌아온 답이, 나한테는 거의 완전히 미지의 세계였다.

- **Corporate Buzzword Satire**: "Synergy", "Circle back", "Let's take this offline" 같은, 알맹이 없는 비즈니스 용어를 비꼬는 콩트
- **"Day in the Life"의 자조판**: "침대에서 안 나오고 Teams 상태 Active 유지하는 법" 같은, 회사 부속품 같은 느낌을 웃음거리로 만드는 영상
- **Corporate Erin 계열**: 냉정한 인사 담당자를 연기하는 캐릭터. 프로페셔널한 미소와 빠른 말투로 정리해고 통보를 포장하는 모노마네
- **LinkedIn Lunatics**: 시(詩)처럼 변해버린 비즈니스 포스팅을, TikTok에서 낭독하면서 까는 콘텐츠

Gemini가 뽑아준 공통점이, 꽂혔다. 영어권 비즈니스 계열 바이럴의 본질은, **"말도 안 되는 기업 문화에 대한, 유머를 통한 반란"**.

이건 MODAY랑, 문화적으로 완전히 같은 땅 위에 있는 영역이었다. "MONDAY: System Booting..." "FRIDAY: Build Successful ✓"라는 티셔츠의 세계관은, 이 컬처 안에 있다.

내 머리만으로 생각했으면, 이 네 가지에는 절대 못 닿았다.

## Codex한테 스토리보드를 그리게 했다

Gemini에서 얻은 정보를, 그대로 Codex한테 넘겼다. "MODAY의 집객용 숏폼 시나리오를, 22초 세로 9:16으로 써줘. 영어권 비즈니스맨 대상, 풍자랑 유머로, 마지막에 브랜드로 착지."

돌아온 게, 이거.

![Storyboard: Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

**"Weekdays Ranked by Developer Damage"**. 요일을, 개발자를 얼마나 망가뜨리는지로 랭킹 매긴다는 컨셉. 티셔츠 제품 소개가 아니라, **밈 영상으로서 완결되는** 구조. 댓글창에서 순위를 두고 논쟁이 벌어진다는 전제로, 마지막에 "Tell me I'm wrong"으로 도발한다. 거기서 처음으로 브랜드명 "MODAY"랑 "Wear the day you survived."가 나온다.

이거, 제품 소개를 **마지막 2초에 숨긴** 설계로 돼 있다. 영상으로서는 광고로 안 보이고, 밈으로 소비되고, 댓글창에서 논쟁이 일어난다. 집객 전략 짜는 건 컨설턴트로서 본업 영역인데, 이번엔 그걸 완전히 AI한테 통째로 던졌다.

게다가 내가 짜는 것보다, 명백히 결이 좋다.

## ChatGPT Image로 모델을 4명 만들었다

영상 시리즈에 필요한 건, **계속 우려먹을 수 있는 모델**. 실사 인물을 고용할 비용도, 촬영할 여유도, 지금은 없다. ChatGPT Image 2.0으로, 4명분의 모델을 한 번에 생성했다.

![Model 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Model 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Model 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Model 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

인종, 나이, 성별을 흩뜨려놨다. 엔지니어다움, 리모트 워커다움, 비즈니스맨다움, 이런 톤은 유지하면서, 네 명 다 다른 분위기를 갖게 했다.

각 모델마다 정면, 사선, 측면, 표정 여러 종까지, 한 번의 프롬프트로 다 나왔다. 이걸 앞으로의 영상에서 돌려쓴다. **4명분의, 우리 브랜드 전속 모델**.

촬영 스튜디오 빌리고, 모델 에이전시 알아보고, 의상 준비하고, 조명 세팅하고. 전부 스킵. 비용은 거의 0원. 소요 시간은 총합 30분 정도.

## 여기서부터는, 손으로 한다

여기서부터 다음 스텝은, 이렇다.

1. 각 씬을, 정지 이미지로 합성한다 (티셔츠 입힌 모델 + 배경)
2. 그 정지 이미지를, 동영상화한다
3. SE랑 자막을 얹는다
4. TikTok / Instagram Reels / YouTube Shorts에 올린다

이번에는, **다국어 전개도, 자동화도, 다음 스텝**에 뒀다. 우선 영어 1편으로, 손으로 만들어서, 한 방 노린다. 맞으면, 그 승리 패턴을 다국어로 스케일시킨다. 자동화 파이프라인을 짠다. 빗나가면, 다른 각도로 다시 친다.

이건 웹 개발 쪽에서 자주 쓰는 작법인데, "**일단 손으로 굴러가는 프로토타입 하나 만들어보고, 승리 패턴이 보이면 자동화에 투자한다**"라는 그거. 집객도 똑같다.

## AI 드리븐이라면서, 손으로 돌아가는 순간이 있다

지난 글에서 "가능한 한 전부 AI한테 넘긴다"라고 썼다. 방침은 안 바꿨다. 이번에도, 스토리보드도, 모델도, 전략 수립도, AI가 짰다.

근데, **영상 합성이랑 편집만큼은, 내 손으로 한다**. 여기를 수동으로 둔 건, 기술적으로 AI로 못 해서가 아니다. **1편의 감을, 내 손으로 잡고 싶어서**다.

뭐가 꽂히는지, 어디서 시청자가 이탈하는지, 댓글창에서 뭐가 벌어지는지. 이걸 내 손으로 관측하지 않으면, 자동화 단계로 넘길 때의 판단 기준을 못 만든다. 손으로 만들고, 맞히고, 빗나가고, 그 경험을 **판단 기준의 재료로 삼는다**.

AI 드리븐 브랜드긴 한데, **판단 기준은 계속 내가 쥔다**. 넘길 타이밍, 안 넘길 타이밍, 그 경계선을 긋는 건 내 일이다. 그리고 지금은, 손을 움직일 타이밍이었다.

참고로, 완성된 1편은 이거.

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

1편이 맞을지 빗나갈지는, 아직 모른다. 맞으면 자동화, 빗나가면 다른 각도. 어느 쪽이든, 여기서부터 새로운 루프가 시작된다.

또 쓸게요.

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
