<!-- canonical: https://moday.me/blogs/journal/first-inquiry-first-loss -->

# 24 horas depois de abrir: as primeiras mensagens, e a primeira venda que eu já perdi

## Abri no dia 18/05. Dois e-mails caíram no dia 19.

Abri a loja no dia 18/05, conforme o plano.

O post anterior terminou com "abrir com o medo ainda pendurado". No dia seguinte à abertura, dois e-mails entraram na caixa.

O primeiro:

> Hi! Quick question — do you ship to Chicago, Dallas, San Jose
> or is your delivery limited to certain areas?
> Also, how long does it usually take for orders to arrive there?

O segundo:

> Can you deliver to Bavaria, Germany?

Vou ser honesto: fiquei *eufórico*.

Chicago, Dallas, San Jose, Baviera. Alguém cujo nome e rosto eu nunca vou conhecer encontrou o caminho até a loja que eu construí, e se interessou o suficiente pra **decidir mandar um e-mail**. Esse tipo de evidência caiu na minha frente pela primeira vez.

## Abri o GA4. Os EUA estavam na frente do Japão.

Em paralelo, fui no GA4. Primeira foto das 24 horas iniciais desde a abertura.

![Usuários do GA4 por país](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/first-inquiry-first-loss-ga4-countries.png)

- United States: 22 usuários (44%)
- Japan: 14 usuários (28%)
- Germany: 6 usuários (12%)
- Singapore: 3 usuários
- Canada: 2 usuários
- South Korea: 1 usuário

O país onde eu moro, aquele que eu fico cutucando na loja todo dia, ficou em **segundo, atrás dos Estados Unidos**. Alemanha em terceiro.

Foi o momento em que o geo-routing e o setup em nove idiomas se pagaram — pela primeira vez, em número. No post anterior eu tinha escrito "não enxergo o cliente". O rosto ainda não está em foco. Mas o **contorno aproximado de onde essas pessoas estão** começou a aparecer.

Pra registro: pedidos ainda estão em zero. O interesse é real, mas não está convertendo. Tem alguma coisa faltando — ansiedade com frete, prazo, preço, visual. Ainda não sei qual, e não vou saber até conseguir observar. É exatamente aqui que eu estou.

## Não consegui responder no mesmo dia.

Voltando aos e-mails.

Os dois caíram. Sou grato. Mas **não consegui responder no mesmo dia em que chegaram**.

Vi tarde da noite, e ainda tinha trabalho do dia-a-dia rodando aquela noite. Rascunhei a resposta em japonês, passei pelo Claude Code pra traduzir pra inglês e alemão, e as mensagens saíram de fato **no dia seguinte**.

O escrever + traduzir em si leva uns 5 a 10 minutos quando você já está com o fluxo montado. Mas a latência entre "e-mail chegou" e "eu estou na frente da tela" já adiciona atraso. Em cima disso, responder uma pergunta sobre disponibilidade de entrega exige conferir os países que a Gelato atende, estimar prazo — montar uma resposta de verdade pede um bloco de foco.

Pra e-mail como canal, responder dentro de 24 horas não é considerado falta de educação. Mas a temperatura do outro lado cai muito em 24 horas.

A diferença entre uma loja onde "você manda uma pergunta e a resposta volta rápido" e uma onde "a resposta vem no dia seguinte" provavelmente muda uma decisão de compra. Especialmente quando é uma marca vista pela primeira vez, envia pra fora do país, e o cliente pagou o custo de escrever em inglês.

Aquilo foi um claro **custo de oportunidade**. O primeiro.

## Então, no mesmo dia, subi um chatbot.

Depois de mandar as respostas atrasadas, me mexi rápido.

**As mesmas perguntas vão voltar.** Disponibilidade de envio, prazo, formas de pagamento, tamanho. Responder uma por uma por e-mail é lento demais como suporte.

Naquele mesmo dia, encaixei um widget de chat no canto inferior direito da loja.

É **construído direto em cima da Claude API**, com suporte a nove idiomas. Embutido no tema do Shopify, ele responde no idioma do visitante automaticamente. Primeira linha de resposta pra envio, prazo, tamanho e pagamento mora ali agora.

Tempo de build: **uns 15 minutos**. Pedi pro Claude Code: "coloca um chat widget no canto inferior direito, roteia as mensagens pela Claude API, ajusta o idioma pelo locale do Shopify do visitante" — e funcionou.

Estado da loja no fim daquele dia: **"se a próxima pergunta igual chegar, o cliente não vai esperar 24 horas"**. Esse foi o movimento disponível no dia.

## O loop de observação começou.

Até esse ponto, toda a fase de construção rodou em cima de "hipóteses que eu tinha montado dentro da minha cabeça".

A camiseta de dia-da-semana tem tudo pra cair bem com engenheiro e geek. Internacional tem que fazer sentido. O modelo de nove idiomas, multi-moeda, estoque zero tem que funcionar. Tudo isso era "tem que".

Isso mudou no segundo em que eu abri.

O GA4 começa a devolver quebra por país. Alguém manda uma pergunta específica por e-mail. Os logs do chat começam a juntar o que os visitantes estão de fato em dúvida.

**O mundo começou a responder.**

Eu ainda não tenho "um jeito de vender". O primeiro custo de oportunidade já aconteceu. Mas porque o loop de observação começou, **o próximo movimento já não é mais chute**.

O começo real de uma marca talvez não seja quando a engenharia termina, nem quando a loja abre — talvez seja quando **o loop de observação começa a girar**, e essa parte é a que começou hoje.

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
