<!-- canonical: https://moday.me/blogs/journal/blog-distribution-pipeline -->

# Un post, nueve idiomas, diez plataformas: la tubería de distribución de MODAY

## Escribo una vez en japonés y aterriza en nueve idiomas, en diez sitios

Esto es lo que pasa cuando termino un borrador en japonés para el devlog de MODAY:

| Capa | Destino |
|---|---|
| Propio | Shopify Blog (JA + 8 locales) |
| Auto, vía API | dev.to / Qiita / Zenn / GitHub devlog |
| Manual, con ficheros listos para pegar | note / Medium / Tumblr |

Mi trabajo, del lado del que escribe, es: terminar el borrador y ejecutar `distribute.py` una vez. El resto se reparte solo.

Monté esta tubería en tres días y la estoy usando desde el primer post. Aquí va la forma real del invento.

## La decisión de diseño: separar «auto» y «manual» desde el principio

Lo primero que tuve claro fue **partir los destinos en dos capas**.

A un lado, plataformas con una API de escritura decente (Shopify, dev.to, Qiita, Zenn-vía-GitHub, GitHub mismo). Al otro, plataformas sin API o con una API hostil (note, Medium, Tumblr). En el momento en que intentas unificar las dos, el script se convierte en un pantano.

Por eso:

- Capa automática — `distribute.py` lo hace todo por HTTP.
- Capa manual — `prepare_handoff.py` escupe **ficheros listos para pegar** que un humano (yo) lleva a la UI.

La capa manual es la parte que aún no he sabido entregarle del todo a la IA. Pero todo lo que ocurre antes del momento del «pegar» está automatizado.

## Qué hace `distribute.py`

El flujo dentro de `distribute.py`:

1. **Hero gate al arrancar**. Si falta `content/posts/<slug>/hero.png`, el script se planta. Sin imagen de cabecera, no hay distribución. Es una protección estructural contra el clásico «uy, se me olvidó el hero».
2. **Publica en el blog Journal de Shopify**: cuerpo + hero en un solo POST.
3. **Registra las traducciones en Shopify**. Lee los ficheros hermanos `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` y mete los ocho locales de golpe vía la API `translationsRegister`.
4. **POST a dev.to**, cuerpo en inglés, reutilizando la URL del CDN de Shopify como cover.
5. **POST a Qiita**, cuerpo en japonés, con `canonical_url` apuntando de vuelta a Shopify.
6. **Zenn — sin llamada a API**. Zenn no expone API de escritura, así que configuré la sincronización Zenn ↔ GitHub. Con un push, el post aparece.
7. **GitHub devlog**: commitea `<slug>-ja.md`, `<slug>-en.md` y `<slug>-hero.png` al repo `moday-devlog`.
8. **Llama a `prepare_handoff.py`** para generar los ficheros de la capa manual.
9. **Escribe `status.json`** al lado del fuente, guardando URL/ID/timestamp de cada plataforma.

Las dos partes con las que me quedo son el **hero gate** y la **ruta Zenn-vía-GitHub**. El hero gate hace estructuralmente imposible publicar un post sin cover. Y Zenn — que a propósito no tiene API de escritura — aun así recibe el post, porque al puente le basta con un `git push`.

## Qué hace `prepare_handoff.py`

Genera ficheros listos para pegar en los tres destinos manuales:

| Fichero | Contenido | Idioma |
|---|---|---|
| `note.md` | Original en JA con comentarios de instrucciones de pegado. Las tablas se convierten en párrafos «**Etiqueta:** valor» porque note no renderiza tablas Markdown. | JA |
| `medium.html` | Traducción EN en HTML. Banner de instrucciones arriba con CSS de no-copiable, cuerpo debajo. ⌘+A → ⌘+C copia solo el cuerpo. | EN |
| `tumblr.md` | Lede en EN (del H1 hasta el primer H2, con tope duro de 1500 caracteres) + canonical + bloque de tags estilo Tumblr. | EN |

La parte no obvia aquí es el **dialecto por plataforma**.

note no renderiza tablas Markdown — si pegas el bruto tal cual, sale `| header | value |` como texto literal y queda horroroso. Por eso `prepare_handoff.py` reescribe cada tabla en párrafos con etiqueta en negrita.

Medium tiene el problema opuesto: al copiar y pegar desde cualquier sitio se arrastra metadata de más. Yo quería poder hacer ⌘+A → ⌘+C en la página y llevarme *solo el cuerpo*. Así que el HTML de salida lleva un banner de instrucciones arriba con CSS `user-select: none` — visible para quien escribe, invisible para el portapapeles.

La cultura de Tumblr no premia volcar un tocho de 3.000 palabras en un post. Así que extraigo solo el lede y enlazo a la canonical.

A cada plataforma se le respeta su **dialecto y su cultura**, en un único sitio centralizado.

## La traducción también la hace la IA — pero dentro de la suscripción

Toda la propuesta de MODAY es «una marca construida en modo AI-driven», así que evidentemente la traducción también va a la IA. Lo que cambié hace poco fue el cómo.

- Antes: `distribute.py` llamaba a la API de Anthropic con Claude Haiku para cada locale.
- Ahora: le pido directamente a Claude Code (Opus 4.7) que «reescriba esto para ocho locales», en la propia sesión.

El motivo es tonto y poco glamuroso: **no quiero pagar una segunda factura medida**. Ya pago Claude Max. Cualquier cosa que pueda pasar dentro de esa suscripción debería pasar dentro de esa suscripción.

Esto, más que una decisión técnica, es una **decisión de negocio**. En un proyecto de una sola persona, lo más importante es contener los costes fijos. Tener una suscripción de Claude Max corriendo *y* a la vez cargos por uso a la API de Anthropic contra la misma tarea es una manera chapucera de llevar la cuenta de resultados personal.

La otra cosa que importó: **calidad**. Lo que salía vía Haiku-API se leía como traducción — usable, pero no nativo. Si me voy a desplegar a nueve idiomas, necesito reescrituras que se lean como si las hubiera escrito un founder local. Sin eso, la marca no aterriza en ninguno de esos mercados.

Ese tipo de reescritura no es traducción; es localización-reescritura. Pasarla por Claude Code con Opus 4.7 me dio una salida claramente mejor que la antigua tubería de Haiku-API.

Bajar el coste, de hecho, subió la calidad. Eso no me lo esperaba.

## El día a día real

El ritmo operativo, ahora mismo, va así:

1. Esbozar un borrador en JA en el Claude móvil (normalmente en el cercanías).
2. En una sesión de Claude Code, dejarlo caer en `webhook/posts/004-<slug>-ja.md`.
3. Pedirle a Claude Code que «reescriba para ocho locales» — produce `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`.
4. Generar el hero con `webhook/generate_hero.py` → `content/posts/<slug>/hero.png`.
5. Ejecutar `python webhook/distribute.py webhook/posts/004-<slug>-ja.md`.
   - Auto-distribuye a Shopify (JA + 8 locales), dev.to, Qiita, GitHub.
   - Llama a `prepare_handoff.py` y deja `content/posts/<slug>/{note.md, medium.html, tumblr.md}`.
6. Abrir note / Medium / Tumblr en el navegador y pegar los ficheros preparados.

El único paso en el que de verdad *pienso* es el 1. El resto son instrucciones a Claude Code, una ejecución de script, y pegar.

## De «se me ocurre una idea en el tren» a «todo publicado», en un día

La parte que más me gusta de esto no es ni siquiera el script — es el **flujo del lado humano**.

Las ideas me caen cuando estoy lejos del escritorio. En el cercanías. Justo antes de dormir. Yendo a algún sitio andando. En ese momento abro el Claude móvil, cargo el proyecto de MODAY y discuto el post hablando con él. Para cuando llego a casa, el borrador está prácticamente terminado.

En la mesa, abro Claude Code, le paso el borrador, él produce las reescrituras por locale y ejecuta la tubería.

El tiempo que paso *sentado en una mesa empujando palabras* es cercano a cero. Esa es la parte de la «marca AI-driven» que ahora mismo se siente real.

## Para cerrar

La tubería misma también la escribió Claude Code. Yo solo dije «quiero un script que distribuya a nueve idiomas y diez plataformas» y fuimos cerrando el spec hablando.

Quedan cosas en la lista: integrar la API de Tumblr, una vista de dashboard del `status.json`, fan-out automatizado a redes sociales. Iré metiendo todo eso sobre la marcha, según vaya rodando la marca.

Más pronto.

— Yoskee  
[moday.me](https://moday.me)

---

<!-- moday-product-card -->
### Ponte el día. — Las camisetas MODAY

| Set | Piezas | Precio |
|---|---|---|
| **[La semana completa →](https://moday.me/collections/bundle-full-week)** | Mon–Sun (7) | $159 |
| **[La semana laboral →](https://moday.me/collections/bundle-workweek)** | Mon–Fri (5) | $119 |
| **[Paquete Inicial →](https://moday.me/collections/bundle-starter)** | Mon · Wed · Fri (3) | $79 |
| **[El fin de semana →](https://moday.me/collections/bundle-weekend)** | Sat · Sun (2) | $55 |

*Envío gratis a partir de $99 · 8 colores × 6 tallas · 9 idiomas*
