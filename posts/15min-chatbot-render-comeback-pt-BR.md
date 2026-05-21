<!-- canonical: https://moday.me/blogs/journal/15min-chatbot-render-comeback -->

# Chatbot pronto em 15 minutos — joguei o Render fora, e voltei a usar

## Da oportunidade perdida no 19/05 até o bot rodando em 15 minutos

Já contei em outro post: no dia 19/05 chegaram as duas primeiras dúvidas de cliente. Não consegui responder no mesmo dia, e a resposta só saiu no dia seguinte.

Encarei isso como uma **oportunidade perdida**, então no mesmo dia montei um chatbot.

Aquele widget clássico que fica no canto inferior direito da loja. Do "vamos fazer" até estar deployado no Shopify rodando, foram cerca de 15 minutos. Vou registrar o que dá pra contar — dentro do que eu mesmo entendo.

## A arquitetura

A grosso modo, é assim:

- **Frontend**: widget no canto inferior direito, dentro do tema Shopify (como exatamente foi implementado, eu não sei)
- **Backend**: Render.com chamando a Claude API
- **Idioma**: amarrado ao locale do Shopify, 9 idiomas
- **Histórico**: gravado numa planilha do Google
- **Escalada**: pergunta que o bot não consegue responder cai no formulário de contato

A filosofia de design é simples: **manter simples**. Só isso. Na fase de empreendedor individual, eu não quero carregar complexidade pra absolutamente nada.

## Joguei o Render fora, e voltei a usar

Em outro post eu avisei: "**tirei o FastAPI / Render do circuito**". Parece contradição, mas o que saiu foi o uso pra **webhook**. O processamento de pedido do Shopify que ia pro Gelato rodava num FastAPI hospedado no Render. Isso foi substituído por outra arquitetura (vai render um post inteiro depois, fica pra outra hora).

O chatbot **ressuscitou o Render**, mas em outra configuração. A infraestrutura que rodava como servidor de webhook, e a que roda agora como API do chatbot — são papéis diferentes, serviços diferentes, processos diferentes. Só estão no mesmo Render.

"Tirei o Render" e "uso o Render" não se contradizem. **É só escolher de novo a ferramenta certa pra cada uso, no momento certo**. Se eu ficar preso em decisão antiga e cravar "não uso mais", o julgamento engessa.

O eixo de decisão tá comigo. A implementação é o Claude Code que monta. A cada remontagem, vou buscar o ótimo daquele momento.

## Por que o histórico vai pra uma planilha do Google

Toda a conversa entre bot e usuário cai numa planilha do Google. Data e hora, locale, pergunta do usuário, resposta do bot, se escalou ou não.

Foi sugestão do Claude Code, e eu aceitei. Pensando depois, foi uma boa por três motivos:

1. **Não quero subir um banco de dados**: precisa modelar schema, tem custo de operação, e pra visualizar precisa de outra coisa. Pesado demais pra fase de empreendedor individual.
2. **Sai de graça**: com uma conta Google, custo zero.
3. **Quando eu for analisar depois, tanto eu quanto o Claude Code conseguimos ler na hora**: dá pra entender só batendo o olho nas colunas.

O terceiro ponto é o mais forte. Quando eu pedir "**resume as tendências das dúvidas recentes**" pro Claude Code, ele lê direto da planilha. Se fosse banco, precisaria escrever script de extração, exportar CSV — sempre um passo a mais.

Um banco dedicado seria mais bonito, mas no tamanho atual a planilha basta. Na fase de empreendedor individual, isso é o **tipo certo de preguiça**.

## Como o suporte a 9 idiomas funciona

Pego o locale atual do Shopify e passo pro bot. O bot bate na Claude API com um prompt do tipo "**responda neste idioma**". Não tem passo de tradução no meio. O Claude escreve direto no idioma.

Em outro post eu escrevi "não é tradução, é localização-rewrite", e isso vale pro bot também. Não é escrever em japonês e traduzir pro português — é responder, desde a primeira palavra, no estilo de quem é nativo da língua. Se for alemão, responde como alemão nativo. Como tudo acontece dentro do modelo, latência de tradução e risco de erro de tradução caem por estrutura.

Aqui também eu não fiz nada de especial. Pedi uma linha: "**pega o locale do Shopify e responde naquele idioma**".

## No prompt eu escrevi "domine as informações do site"

O bot consegue responder sobre o que está no site da MODAY e sobre os produtos do Gelato. Disponibilidade de envio, prazo, tamanhos, formas de pagamento, política de devolução, preços, composição das bundles.

Pedi pro Claude Code "**domine isso**".

Sendo honesto: **eu não sei dizer como ele fez pra dominar**. Se ficou embutido no prompt, se ele faz fetch do site, se combina os dois — quem decidiu e implementou foi o Claude Code.

Como já escrevi em outro post: dei a direção, deixei a implementação com ele. Tá rodando, as respostas vêm decentes, então por enquanto tá bom assim. Se quebrar, eu falo "conserta" pro Claude Code.

## O que ele não responde, manda pro formulário de contato

Deixar o bot responder tudo é perigoso.

Consultas individuais sobre tamanho específico, embrulho pra presente, venda corporativa, problemas com pedido. Se o bot cravar nessas áreas, depois vira atrito.

Quando o bot avalia que "é melhor não responder essa", ele direciona pro formulário de contato. O desenho dos guard-rails também ficou com o Claude Code. Eu só pedi uma linha: "**se for pergunta que não dá pra responder, manda pro formulário de contato**".

Quais perguntas o bot responde, e quais escalam — quem traçou essa linha foi o Claude Code. De tempos em tempos eu olho o log, e se aparecer alguma divisão claramente esquisita, eu ajusto. Por enquanto não apareceu nada.

15 minutos foi possível porque, dentro desses 15 minutos, sobraram poucas coisas pra eu pensar.

"Widget no canto inferior direito", "base na Claude API", "9 idiomas", "ressuscita o Render", "histórico na planilha", "escala pro formulário de contato". Decididos esses pontos, o resto o Claude Code monta. Eu dou o GO e confirmo se rodou.

No segundo dia depois de abrir a loja, a base de automação do suporte começou a girar. O primeiro item do "**1 melhoria por dia**" foi esse.

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
