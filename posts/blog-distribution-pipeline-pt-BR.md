<!-- canonical: https://moday.me/blogs/journal/blog-distribution-pipeline -->

# Um post em japonês, nove idiomas, dez canais: o pipeline de distribuição da MODAY

## Escrevo um rascunho em japonês e ele aterrissa em nove idiomas, em dez lugares

Quando termino um rascunho em japonês pro devlog da MODAY, o que acontece é mais ou menos isso:

| Camada | Destino |
|---|---|
| Próprio | Shopify Blog (JA + 8 locales) |
| Distribuição automática via API | dev.to / Qiita / Zenn / GitHub devlog |
| Manual, com arquivo pronto pra colar | note / Medium / Tumblr |

Do meu lado, o trabalho é: terminar o rascunho e rodar `distribute.py` uma vez. O resto se espalha sozinho.

Montei esse pipeline em três dias e estou usando desde o primeiro post. Vou descrever exatamente o formato que ele tem hoje.

## A decisão de design: separar "auto" e "manual" desde o começo

A primeira escolha foi **dividir os destinos em duas camadas**.

De um lado, plataformas com uma write API que funciona (Shopify, dev.to, Qiita, Zenn-via-GitHub, o próprio GitHub). Do outro, plataformas sem API ou com API hostil (note, Medium, Tumblr). Na hora em que você tenta unificar isso num script só, vira pântano.

Então:

- Camada auto — `distribute.py` faz tudo via HTTP
- Camada manual — `prepare_handoff.py` cospe **arquivos prontos pra colar**, e um humano leva até a UI

A camada manual é a parte que eu ainda não consegui passar pra IA. Mas tudo até o instante do paste já está automatizado.

## O que o `distribute.py` realmente faz

O fluxo dentro do `distribute.py`:

1. **Hero gate na largada**. Se `content/posts/<slug>/hero.png` não existir, o script para na hora. Sem imagem de capa, sem distribuição. É uma trava estrutural contra "ih, esqueci a hero".
2. **Posta no blog Shopify Journal**, corpo + hero numa tacada só.
3. **Registra as traduções no Shopify**. Lê os arquivos irmãos `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` e empurra todos os oito locales de uma vez via API `translationsRegister`.
4. **POST no dev.to**, corpo em EN, reusando a URL CDN do Shopify como cover.
5. **POST no Qiita**, corpo em JA com `canonical_url` apontando de volta pro Shopify.
6. **Zenn — sem chamada de API**. O Zenn não expõe write API, então deixei configurado o sync Zenn ↔ GitHub. Um push e o post nasce automático.
7. **GitHub devlog**: comita `<slug>-ja.md`, `<slug>-en.md`, `<slug>-hero.png` no repo `moday-devlog`.
8. **Chama `prepare_handoff.py`** pra gerar os arquivos de paste da camada manual.
9. **Escreve `status.json`** ao lado da fonte, registrando URL/ID/timestamp de cada plataforma.

As duas partes de que eu mais gosto são o **hero gate** e a **rota Zenn-via-GitHub**. O hero gate torna estruturalmente impossível subir um post sem capa. E o Zenn — que de propósito não oferece write API — recebe o post mesmo assim, porque um `git push` é a ponte de que ele precisa.

## O que o `prepare_handoff.py` faz

Gera arquivos prontos pra colar nos três destinos manuais:

| Arquivo | Conteúdo | Idioma |
|---|---|---|
| `note.md` | Original em JA com comentários de instrução de paste. As tabelas viram parágrafos no formato "**Rótulo:** valor" porque o note não renderiza tabela Markdown. | JA |
| `medium.html` | Tradução EN em HTML. Banner de instruções no topo com CSS de copy-disabled, corpo embaixo. ⌘+A → ⌘+C copia só o corpo. | EN |
| `tumblr.md` | Lede em EN (H1 até o primeiro H2, capado em 1500 caracteres) + canonical link + bloco de tags no estilo Tumblr. | EN |

A parte não-óbvia aqui é o **dialeto de cada plataforma**.

note não renderiza tabela Markdown — se você cola a coisa crua, aparece `| header | value |` como texto literal, fica horrível. Por isso o `prepare_handoff.py` reescreve toda tabela em parágrafos com rótulo em bold.

Medium tem o problema oposto: copy-paste de qualquer fonte tende a arrastar metadado junto. Eu queria que o redator (eu) conseguisse fazer ⌘+A → ⌘+C na página e levar *só o corpo*. Então o HTML de saída tem um banner de instruções no topo com `user-select: none` — visível pro redator, invisível pro clipboard.

A cultura do Tumblr não recompensa quem despeja um ensaio de 3.000 palavras. Então eu corto só o lede e linko de volta pro canonical.

Cada plataforma recebe o **dialeto e a cultura** dela respeitados, num único lugar centralizado.

## A tradução também é IA — mas dentro da assinatura

O pitch inteiro da MODAY é "construção de marca dirigida por IA", então é claro que a tradução também vai pra IA. Mudei o "como" recentemente.

- Antes: `distribute.py` chamava a Anthropic API com Claude Haiku pra cada locale.
- Agora: peço pro Claude Code (Opus 4.7) direto na sessão, "reescreve isso pros oito locales".

O motivo é burro e nada sexy: **não quero uma segunda conta com medidor rodando**. Eu já pago Claude Max. O que conseguir acontecer dentro dessa assinatura, deveria acontecer dentro dela.

Isso é menos uma decisão técnica e mais uma **decisão de gestão**. Pra uma operação de uma pessoa só, o mais importante é manter custo fixo baixo. Rodar Claude Max *e* cobrança medida da Anthropic API contra a mesma tarefa é uma forma desleixada de tocar o P&L pessoal.

A outra coisa que pesou: **qualidade**. As saídas do Haiku via API liam como tradução — utilizáveis, mas não nativas. Pra ir pra nove locales, eu preciso de rewrites que leiam como se um founder local tivesse escrito ali. Sem isso, a marca não cola em nenhum desses mercados.

Esse tipo de rewrite não é tradução, é localização-rewrite. Rodar pelo Claude Code no Opus 4.7 me deu uma saída sensivelmente melhor que o pipeline antigo Haiku-API.

Cortar custo, na prática, aumentou a qualidade. Não esperava por essa.

## O dia a dia operacional

O ritmo de operação hoje fica assim:

1. Rascunho um post em JA pelo Claude mobile (em geral no trem).
2. Numa sessão de Claude Code, deposito em `webhook/posts/004-<slug>-ja.md`.
3. Peço pro Claude Code "reescrever pros oito locales" — ele produz `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`.
4. Gero a hero com `webhook/generate_hero.py` → `content/posts/<slug>/hero.png`.
5. Rodo `python webhook/distribute.py webhook/posts/004-<slug>-ja.md`.
   - Auto-distribui pra Shopify (JA + 8 locales), dev.to, Qiita, GitHub.
   - Chama `prepare_handoff.py` que cospe `content/posts/<slug>/{note.md, medium.html, tumblr.md}`.
6. Abro note / Medium / Tumblr no navegador e colo os arquivos prontos.

A única etapa em que eu de fato *penso* é a 1. O resto é instrução pro Claude Code, um script, e Ctrl+V.

## Da "ideia no trem" pra "tudo no ar" no mesmo dia

A parte de que eu mais gosto nisso nem é o script — é o **fluxo do lado humano**.

As ideias me pegam longe da mesa. No trajeto, antes de dormir, andando. Nessas horas eu abro o Claude mobile, puxo o projeto MODAY e converso o post. Quando chego em casa, o rascunho está praticamente pronto.

Na mesa, abro o Claude Code, entrego o rascunho, ele produz os rewrites por locale e dispara o pipeline.

O tempo que eu passo *sentado, empurrando palavra* é quase zero. Essa é a parte de "construção de marca dirigida por IA" que, hoje, soa real de verdade.

## Pra fechar

O pipeline em si também foi escrito pelo Claude Code. Eu só disse "quero um script que distribua pra nove idiomas e dez plataformas", e a gente foi acertando a spec na conversa.

Ainda tem coisa na lista: integração com API do Tumblr, dashboard pra ler o `status.json`, fan-out automático pra rede social. Vou encaixando essas no caminho.

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
