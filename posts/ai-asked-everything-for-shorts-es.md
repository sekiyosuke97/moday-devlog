<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# Para hacer vídeos cortos, le pregunté a la IA absolutamente todo lo que no sabía

## Me retracto de lo del «bucle de observación»

En un post anterior escribí que «el bucle de observación se había puesto en marcha» — que en el momento en el que abrimos, el mundo había empezado a contestar.

Cuatro o cinco días después, lo que de verdad he sacado en claro es esto: **la muestra es demasiado pequeña como para observar nada**.

Puedo quedarme mirando GA4, seguir el comportamiento del carrito, escarbar los logs del chatbot — pero el volumen es tan bajo que de ahí no sale ninguna hipótesis con la que merezca la pena moverse. Para empezar a teorizar siquiera, tiene que entrar más gente.

Así que la jugada correcta no es observar todavía. Es **subir el tráfico primero**. Tenía el orden equivocado.

## Toca arremangarse para captar tráfico

Toda la fase de construcción había ido sobre **montar la máquina**. Distribución en nueve idiomas por diez canales, chatbot automatizado, automatización pedido→producción, bucle de mejora automatizado. Todo bajo la misma idea: «monta el sistema, luego deja que corra».

Quería que la captación funcionara igual — entra el presupuesto en publi, se acumulan datos, la IA propone mejoras, se automatiza el bucle, listo.

Pero ahora mismo no hay presupuesto publicitario (eso ya lo conté en otro post). Con la publi de pago descartada, **lo único que queda es lo orgánico en redes**. Vídeo corto en concreto — para un producto tan visual como este, el formato debería encajar.

Salvo por un pequeño detalle: **no tengo ni idea de qué funciona ahora mismo en vídeo corto**.

No veo cortos en japonés de forma habitual. ¿Cortos en inglés? Menos todavía. Me dedico profesionalmente a la consultoría de e-commerce, y esta es una debilidad que toca asumir tal cual. Me estoy metiendo en un terreno que no es mi punto fuerte.

## Paso uno: preguntarle a Gemini

Justo había estado siguiendo las noticias del Google I/O y me apetecía una excusa para meterle caña a Gemini. Así que le pregunté: «¿Qué está petando ahora mismo en vídeo corto dirigido a profesionales angloparlantes en TikTok, LinkedIn y Shorts?».

Lo que volvió era un mundo que yo desconocía por completo:

- **Corporate Buzzword Satire** — sketches que se burlan del vocabulario hueco del corporate-speak: «Synergy», «Circle back», «Let's take this offline».
- **«Day in the Life» en clave autoparódica** — del estilo «cómo mantener Teams en Active sin salir de la cama», riéndose de la sensación de ser una pieza más del engranaje.
- **Personajes tipo Corporate Erin** — actrices interpretando a la RR. HH. fría, sonrisa profesional y verborrea rápida envolviendo un despido con cadencia alegre.
- **LinkedIn Lunatics** — gente leyendo en alto y parodiando en TikTok esos posts «poetizados» de negocios que la gente publica en LinkedIn con toda la seriedad del mundo.

El patrón que sacó Gemini me pegó fuerte. La columna vertebral de la viralidad humorística angloparlante de oficina es **«motín cómico contra una cultura corporativa absurda»**.

Y eso, por definición, es territorio limítrofe con MODAY. El universo de una camiseta «MONDAY: System Booting...» o «FRIDAY: Build Successful ✓» vive dentro de esa misma cultura.

De mi cabeza, sola, jamás habría salido a esos cuatro géneros.

## Paso dos: pasárselo a Codex y pedirle un storyboard

Cogí lo que me dio Gemini y se lo metí directamente a Codex. Prompt: «Escribe el storyboard de un vídeo corto de captación para MODAY. Formato vertical 9:16, 22 segundos, público angloparlante de oficina, tono de sátira y humor, aterrizando al final en la marca».

Lo que me devolvió:

![Storyboard: Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

**«Weekdays Ranked by Developer Damage»**. Concepto: rankear los días de la semana según cuánto destrozan a un programador. No es un escaparate de producto — es un **meme que se sostiene solo**. Diseñado para que los comentarios se pongan a discutir el ranking, rematado con un «Tell me I'm wrong» de cebo. Solo al final aterriza la marca: «MODAY — Wear the day you survived».

El pitch de producto está **escondido en los dos últimos segundos**. El vídeo no se lee como anuncio. Se consume como meme. Los comentarios hacen el trabajo. La estrategia de captación cae de lleno en mi terreno como consultor — y esta vez se la he externalizado por completo a la IA.

Y el resultado es claramente mejor que lo que habría dibujado yo.

## Paso tres: generar cuatro modelos reutilizables en ChatGPT Image

Una serie de vídeos necesita **personajes que puedas reutilizar**. No puedo permitirme contratar gente real, y no tengo tiempo para rodar. ChatGPT Image 2.0 me generó cuatro modelos en una sola tanda.

![Modelo 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Modelo 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Modelo 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Modelo 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

Etnia, edad y género repartidos entre los cuatro. Cada uno mantiene un aire coherente — tono ingeniero, tono curra-en-remoto, tono profesional de oficina —, pero cada modelo tiene su propia cara.

Cada uno vino con plano frontal, tres cuartos y perfil, además de varias expresiones, todo a partir de un único prompt. Son el reparto fijo de la serie de vídeos. **Cuatro modelos de la casa, exclusivos de la marca.**

Alquilar estudio. Llamar a una agencia. Conseguir vestuario. Montar iluminación. Todo saltado. El coste es esencialmente cero. Tiempo total, unos treinta minutos.

## A partir de aquí, lo hago a mano

Los pasos que quedan:

1. Componer cada escena como imagen fija (modelo + la camiseta + fondo).
2. Animar la imagen fija para convertirla en vídeo.
3. Añadir SFX y subtítulos.
4. Publicar en TikTok / Instagram Reels / YouTube Shorts.

En esta ronda, el **fan-out multilingüe y la automatización quedan para la siguiente etapa**. Primero un vídeo en inglés, hecho a mano, soltado a ver qué pasa. Si pega, escalo el patrón ganador a los nueve idiomas y monto la pipeline de automatización por detrás. Si no pega, pruebo otro ángulo.

Esto sale directamente del manual del desarrollo web: **monta primero un prototipo funcional a mano, y solo inviertes en automatización cuando ya ves la forma de lo que gana**. La captación se rige por la misma regla.

## AI-driven, pero todavía vuelvo a mis propias manos

En un post anterior escribí: «delegar en la IA todo lo que se pueda». Esa política no ha cambiado. En esta ronda el storyboard, los modelos y la estrategia los ha construido la IA.

Pero **la composición y la edición del primer vídeo las hago yo, a mano**. No porque técnicamente la IA no pueda. Porque **quiero la textura del primero en mis propias manos**.

Qué engancha. Dónde se cae el espectador. Qué hacen los comentarios. No puedo desarrollar el criterio para la fase de automatización si no lo veo ocurrir personalmente. Construir a mano, acertar, fallar, registrar la experiencia — eso es **la materia prima de los criterios** que voy a necesitar después.

La marca es AI-driven, pero **el criterio sigue siendo mío**. Cuándo delegar y cuándo no — esa frontera la dibuja el founder. Y ahora mismo es uno de esos momentos de «esto se hace a mano».

Para el que tenga curiosidad, este es el primer vídeo:

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

Si el primero pega o se estampa, todavía no lo sé. Pega → automatización. Se estampa → otro ángulo. Pase lo que pase, desde aquí arranca un bucle nuevo.

Pronto más.

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
