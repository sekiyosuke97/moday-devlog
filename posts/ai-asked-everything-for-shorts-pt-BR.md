<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# Pra fazer vídeo curto, perguntei tudo que eu não sabia pra IA

## Voltando atrás no que eu disse sobre "o loop de observação"

Num post anterior eu escrevi que "o loop de observação começou a girar" — que, do segundo em que a loja abriu, o mundo passou a responder.

Quatro, cinco dias depois, caiu a ficha: **o tamanho da amostra é pequeno demais pra observar qualquer coisa.**

Posso encarar o GA4, seguir o comportamento de carrinho, garimpar os logs do chatbot — o volume é tão baixo que nada disso gera hipótese que valha agir em cima. Pra começar a teorizar de verdade, mais gente precisa entrar.

Ou seja, o passo certo agora não é observar. É **subir o tráfego primeiro.** Eu tinha invertido a ordem.

## Hora de botar a mão pra trabalhar em aquisição

A fase de construção inteira foi sobre **montar a máquina**. Distribuição em nove idiomas e dez plataformas, chatbot automatizado, fluxo automático de pedido→produção, loop de melhoria automatizado. Tudo arquivado em "constrói o sistema, depois deixa rodar".

Eu queria que aquisição funcionasse no mesmo molde — verba de mídia entra, dado acumula, IA propõe melhoria, automatiza o loop, pronto.

Só que verba de mídia não existe agora (já falei disso em outro post). Sem pago em cima da mesa, **o único canal que sobra é social orgânico**. Vídeo curto, especialmente — pra um produto tão visual quanto esse, o formato tem tudo pra encaixar.

Tem um detalhe, porém: **eu não tenho a menor ideia do que funciona em short-form hoje.**

Não acompanho shorts em japonês de forma constante. Shorts em inglês? Menos ainda. Vivo de consultoria de e-commerce e essa é uma fraqueza que eu só posso assumir. Estou pisando num terreno que não é o meu forte.

## Passo um: perguntar pro Gemini

Eu estava acompanhando as notícias do Google I/O e queria uma desculpa pra colocar o Gemini pra trabalhar. Joguei a pergunta: "O que está em alta em vídeo curto pra público de profissionais de negócios em inglês, no TikTok, LinkedIn e Shorts?"

O que voltou foi um mundo que eu desconhecia por completo:

- **Corporate buzzword satire** — esquetes zoando o vocabulário oco do corporativês: "Synergy", "Circle back", "Let's take this offline".
- **"Day in the Life" autoconsciente** — vinhetas tipo "como manter o Teams 'Active' sem sair da cama", rindo daquele sentimento de engrenagem.
- **Personagens estilo Corporate Erin** — atores fazendo o RH frio, sorriso profissional e fala rápida embalando uma demissão em tom alegre.
- **LinkedIn Lunatics** — gente no TikTok lendo em voz alta e zoando aqueles posts de negócio poetizados que o pessoal publica sério no LinkedIn.

O padrão que o Gemini extraiu acertou em cheio. A espinha dorsal da viralização de humor corporativo em inglês é **"motim cômico contra a cultura corporativa absurda".**

Isso é território vizinho do MODAY por definição. A visão de mundo de uma camiseta "MONDAY: System Booting…" e de uma "FRIDAY: Build Successful ✓" vive dentro dessa mesma cultura.

Não tinha como eu chegar nesses quatro gêneros trabalhando só com a minha cabeça.

## Passo dois: jogar pro Codex e pedir o storyboard

Passei o output do Gemini direto pro Codex. Prompt: "Escreva o storyboard de um short de aquisição pro MODAY. 9:16 vertical, 22 segundos, público de profissionais que falam inglês, tom de sátira e humor, aterrissa na marca no final."

O que voltou foi isto:

![Storyboard: Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

**"Weekdays Ranked by Developer Damage".** Conceito: rankear os dias da semana pelo tanto de estrago que causam num desenvolvedor. Não é vitrine de produto — é um **meme que se sustenta sozinho**. Construído pra que a seção de comentários comece a brigar pelo ranking, fechando com "Tell me I'm wrong" como isca. Só no final a marca pousa: "MODAY — Wear the day you survived."

A pitch do produto está **escondida nos dois últimos segundos**. O vídeo não lê como anúncio. É consumido como meme. Os comentários fazem o trabalho. Pensar estratégia de aquisição é exatamente o que eu faço no dia a dia como consultor — e dessa vez terceirizei completamente pra IA.

E o resultado é nitidamente melhor do que o que eu teria rascunhado.

## Passo três: gerar quatro modelos reutilizáveis no ChatGPT Image

Uma série de vídeos precisa de **personagens que dá pra reaproveitar**. Não tenho como contratar gente de verdade, nem tenho tempo de gravar. O ChatGPT Image 2.0 gerou quatro modelos pra mim numa tacada só.

![Model 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Model 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Model 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Model 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

Etnia, idade e gênero espalhados entre os quatro. Cada um mantém uma vibe coerente — cara de engenheiro, cara de remote-worker, cara de profissional de escritório — mas cada modelo tem rosto próprio.

Cada um veio com ângulo frontal, três-quartos e perfil, além de várias expressões, tudo num prompt só. Esses são o elenco recorrente da série. **Quatro modelos da casa, exclusivos da marca.**

Alugar estúdio. Procurar agência. Garimpar figurino. Montar iluminação. Pulei tudo. Custo é praticamente zero. Tempo total, uns trinta minutos.

## Daqui pra frente, eu vou na mão

Os passos que sobraram:

1. Compor cada cena como still (modelo + camiseta + fundo).
2. Animar o still virando vídeo.
3. Colocar SFX e legendas.
4. Postar no TikTok / Instagram Reels / YouTube Shorts.

Pra esta rodada, eu empurro **fan-out multi-idioma e automação pro próximo passo**. Um vídeo em inglês primeiro, feito na mão, lançado pra ver o que volta. Se acertar, eu escalo o padrão vencedor pros nove idiomas e monto a pipeline de automação por trás. Se não, tento outro ângulo.

Isso saiu direto do manual de web dev: **constrói um protótipo funcionando na mão, e só investe em automação quando você consegue enxergar o formato que vence.** Aquisição obedece a mesma regra.

## Movido a IA, mas eu volto pras minhas mãos

Já escrevi num post anterior: "entregar pra IA tudo que der pra entregar". A política não mudou. Nesta rodada, o storyboard, os modelos e a estratégia foram todos construídos por IA.

Mas **a composição e a edição do primeiro vídeo, eu faço na mão.** Não porque a IA tecnicamente não daria conta. Porque **eu quero a textura do primeiro nas minhas próprias mãos.**

O que prende. Onde o espectador cai fora. O que rola na seção de comentários. Não tem como eu desenvolver o critério pra fase de automação se eu não vir acontecer pessoalmente. Construir na mão. Acerto, erro, anota a experiência — esse é **o material bruto pros critérios** que eu vou precisar lá na frente.

A marca é movida a IA, mas **o julgamento continua sendo meu.** Quando delegar, quando não — esse limite é trabalho de founder. E agora é um dos momentos "faça na mão".

Pra quem tiver curiosidade, o primeiro vídeo está aqui:

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

Se o primeiro pega ou afunda, ainda não sei. Acertou → automação. Errou → outro ângulo. Em todo caso, um loop novo começa aqui.

Até a próxima.

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
