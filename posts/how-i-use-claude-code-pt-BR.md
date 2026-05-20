<!-- canonical: https://moday.me/blogs/journal/how-i-use-claude-code -->

# Como eu uso o Claude Code — não organizo, delego, vou no feeling

## Olhando pra trás, vale registrar como eu uso o Claude Code

Já escrevi bastante sobre a construção da MODAY até aqui, mas nunca cheguei a contar **como eu opero o Claude Code no dia a dia**.

A escolha de stack, a pipeline de distribuição, a localização em 9 idiomas, o chatbot que ficou pronto em 15 minutos — tudo isso ficou no lado do "**o que foi construído**".

Agora que a loja está no ar e eu já entrei em fase de operação, é hora de subir um pouco a câmera e olhar pro processo.

Spoiler do final: **não organizo, delego, vou no feeling**.

Provavelmente é o oposto da maioria dos tutoriais de Claude Code que você vê por aí.

## O CLAUDE.md foi o próprio Claude que escreveu

Por aí dizem: "**escreva um CLAUDE.md bem organizado com as informações do projeto**". Brand, stack técnica, padrões de código, prioridades. O humano organiza o contexto pro Claude Code entender o projeto. É mais ou menos o padrão recomendado.

No CLAUDE.md da MODAY, **não tem uma linha sequer que eu tenha escrito**. Nem sei direito o que tem lá dentro.

No começo da construção, eu disse pro Claude Code "fique à vontade pra arrumar o arquivo do jeito que quiser". Ele foi montando sozinho: informações de marca, stack técnica, tabela de SKU, configuração de Markets, prioridades por fase. Quando eu olho de vez em quando, tá num formato que provavelmente o Claude lê melhor do que se eu tivesse organizado na mão.

Do começo ao fim, eu não fiz absolutamente **nenhum trabalho de "organização"**. **Eu passei a própria tarefa de organizar pro lado do Claude**.

## As sessões eu separo "no feeling"

Eu separo sessões, sim. Mas **sem regra nenhuma**.

Não existe divisão rígida por objetivo. Funciono num esquema mais ou menos assim: "produção de conteúdo", "melhoria de UI/UX", "MD (trabalho miscelâneo)". Geração de imagem, tradução e código convivem dentro da mesma sessão sem problema.

Não divido por papel ("sessão de tradução", "sessão de código"). **Divido pelo fluxo do trabalho**. Parece bagunça, mas o efeito colateral é que o "encadeamento de ideias" flui sem corte.

Tô mexendo numa UI e me toca: "ah, faz sentido ajustar a tradução pra combinar com isso". Já rodo a tradução na mesma sessão. Como o custo de carregar contexto entre sessões é zero, **o fluxo de decisão não quebra**. Isso, surpreendentemente, faz uma diferença grande.

## Instrução técnica, eu quase não dou

Já comentei em outro post: na hora de escolher a stack, eu não dei nenhuma condição técnica. Tudo o que coloquei foram condições de negócio. Depois que entramos na implementação, essa postura não mudou.

A única coisa que eu faço questão de comunicar é: "**use Shopify e Gelato do jeito padrão, implementação original só o mínimo necessário**".

Pra mim, isso é regra de ouro de SaaS. Usar dentro do escopo que o vendor imaginou é o que se mantém estável no longo prazo. Implementação custom é tentadora no curto prazo, mas quebra na próxima atualização do vendor. Fluxo padrão, API padrão, estrutura de tema padrão. Só foge disso quando é realmente necessário.

Comunicando só isso, o resto — como chamar a API, estratégia de teste, error handling, detalhe da implementação — eu passo praticamente tudo pro Claude Code.

## Quando ele pergunta "me ensina isso", eu respondo "faz você"

O Claude Code às vezes vem pedir confirmação. "Pode me mostrar o conteúdo desse arquivo?", "Tá bom assim?", "Como você quer o teste?".

Pra quase tudo isso eu respondo: "**faz você**".

Se quer ver o arquivo, abre o view sozinho. Se tá pedindo decisão, "decide você". Resultado: na maioria das vezes ele vai ler, decide sozinho, e segue até a implementação.

Isso é a prática daquilo que escrevi em outro post: "**quero passar a iniciativa pro lado da AI**". Não devolvo decisão, dou pra ele decidir.

O que sobra no final pra mim é só **o que realmente não tem como rodar via API**. Conta bancária, análise de pagamento, cadastro nos serviços, registro de cobrança, geração de chave de API. Essas coisas só dá pra contratar como pessoa física, então aí eu mexo. Fora isso, tudo fica do lado do Claude.

## Faço o Claude patrulhar o GA4 todo dia e sugerir melhorias

Essa rotina começou depois da abertura.

Todo dia o Claude Code patrulha o GA4 e **gera problemas e propostas de melhoria**. Eu só passo o olho e descarto o que claramente não faz sentido. Os 60–70% que sobram, ele implementa na hora.

Da proposta até a implementação, o que eu faço é só dar GO/NG. Escrever código, pensar arquitetura — quase zero.

Eu quero adotar isso como conceito de operação: "**no mínimo 1 melhoria implementada por dia**". Desde o instante em que a loja abriu, todo dia alguma coisa melhora. Uma marca onde o loop de melhoria não para tende a ficar forte no longo prazo — é a aposta.

E 99% desse loop é o Claude Code quem roda.

## Não organizo, mas tá organizado

Escrevendo isso tudo, reparo de novo: eu praticamente não pratico nenhum dos rituais clássicos de desenvolvimento — "organização", "design", "planejamento".

Não escrevi CLAUDE.md. As sessões são no feeling. Workflow não está rotinizado. Não tem diagrama técnico, não tem ferramenta de gestão de tarefa. Mesmo assim, da construção à operação, as coisas seguem rodando.

Mais preciso: **a organização eu deleguei pro lado do Claude**. Eu não faço, mas o Claude Code organiza. Por isso, no resultado final, o estado organizado se mantém.

Essa estrutura lembra aquela cena clássica do Masayoshi Son: ele fala "vamos fazer" e um time de execução absurdamente competente entra em ação, organiza e implementa tudo. **Eu fico no lado do "vamos fazer", e o time de execução virou AI**.

Esse é, na real, o aprendizado mais forte dessas três semanas: na era da AI, um indivíduo consegue reproduzir essa estrutura.

## Pra fechar

Não acho que esse seja o jeito "certo" de fazer. Provavelmente também funciona escrever um CLAUDE.md caprichado, separar sessões por objetivo, rotinizar o workflow.

Só que, no meu caso, **não organizar foi mais rápido**. Em vez de gastar tempo organizando, prefiro jogar pro Claude Code e usar esse tempo pra julgar o que ele me devolve.

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
