<!-- canonical: https://moday.me/blogs/journal/15min-chatbot-render-comeback -->

# Un chatbot en 15 minutos — había dejado Render, y acabé volviendo a usarlo

## De la oportunidad perdida del 19/5 al bot funcionando en 15 minutos

Lo conté en otro post: el 19 de mayo entraron las dos primeras consultas a la tienda.
No conseguí responder ese mismo día y la respuesta acabó saliendo al día siguiente.
Eso lo registré como **oportunidad perdida**, así que ese mismo día monté un chatbot.

El típico widget que se pone en la esquina inferior derecha de la tienda.
Desde que abrí el editor hasta que estaba desplegado en Shopify y atendiendo: unos 15 minutos.
Cuento lo que sé de cómo está hecho por dentro.

## Arquitectura

A grandes rasgos, así está montado:

- **Frontend**: widget abajo a la derecha en el tema de Shopify (no tengo claro cómo lo implementó por dentro)
- **Backend**: en Render.com, llamando a la API de Claude
- **Idioma**: ligado al locale de Shopify, 9 idiomas
- **Historial**: se guarda en una hoja de Google Sheets
- **Escalado**: las preguntas que no puede contestar se derivan al formulario de contacto

La filosofía de diseño es simple: **mantenerlo simple**. Y nada más.
En fase de proyecto unipersonal, hagas lo que hagas, no quieres cargar con cosas complicadas.

## Había dejado Render, y acabé volviendo a usarlo

En otro post anuncié que «**FastAPI / Render ya está fuera**».
Suena contradictorio, pero lo que saqué fue el uso como **webhook**.
El procesamiento que recibía los pedidos de Shopify y los empujaba a Gelato corría en un FastAPI sobre Render.
Eso lo sustituí por otra arquitectura (esa historia da para un post entero, que ya escribiré).

El chatbot **resucita ese Render, pero con otra configuración**.
La infra que corría como servidor de webhooks y la infra que corre como API del chatbot.
Los roles son distintos, son servicios distintos, procesos distintos.
Lo único que comparten es que están sobre Render.

«He sacado Render» y «estoy usando Render» no se contradicen.
Es solo que **para cada uso eliges, en ese momento, la herramienta más adecuada**.
Si te atas a una decisión pasada y declaras «esto no vuelvo a usarlo», tu criterio se vuelve rígido.

El criterio lo tengo yo. La implementación la monta Claude Code.
Cada vez que rehacemos algo, vamos a buscar el óptimo del momento.

## El historial se guarda en Google Sheets

Todas las conversaciones entre el bot y el usuario se escriben en una hoja de Google.
Fecha y hora, locale, pregunta del usuario, respuesta del bot, si se escaló o no.

Esto fue una propuesta de Claude Code que acepté.
Visto en retrospectiva, encajaba bien por tres razones:

1. **No quiero montar una base de datos**: hay que diseñar el esquema, cuesta operarla, y encima necesitas algo aparte para visualizar. Demasiado peso para esta fase
2. **Sale gratis**: con tener una cuenta de Google, coste cero
3. **Cuando luego quiera analizar, tanto yo como Claude Code lo leemos al momento**: con mirar las columnas, ya está todo

El tercer punto es el grande.
Cuando le pida a Claude Code «**resúmeme las tendencias de las consultas recientes**»,
puede ir a leer directamente la hoja.
Con una base de datos habría que escribir un script de extracción, exportar a CSV, un paso más.

Una BBDD propia quedaría más limpia, pero al tamaño de hoy un Sheets sobra.
En fase de proyecto unipersonal, esto es lo que llamo **vaguería bien hecha**.

## Cómo está hecho el soporte a 9 idiomas

Se obtiene el locale actual de Shopify y se le pasa al bot.
El bot llama a la API de Claude con un prompt del tipo «**contesta en este idioma**».
No hay paso intermedio de traducción. Claude escribe directamente en ese idioma.

En otro post escribí «no es traducción, es localización-reescritura», y eso aplica también al bot.
No se escribe en japonés para luego traducir al inglés: desde el principio se responde con el estilo de un nativo en inglés.
Si toca alemán, contesta como nativo alemán.
Como todo pasa dentro del modelo, la latencia de traducción y el riesgo de errores se reducen por estructura.

Aquí tampoco hice nada especial.
Solo una línea: «**recibe el locale de Shopify y responde en ese idioma**».

## En el prompt puse «entiende lo que hay en la web»

El bot puede responder con la información publicada en la web de MODAY y con los datos de producto de Gelato.
Si envía o no, plazos, tallas, métodos de pago, política de devoluciones, precios, composición de los bundles.

Le pedí a Claude Code que «**lo entendiera**».

Por honestidad lo digo: **cómo se lo hizo entender, yo no lo sé**.
Si está embebido en el prompt, si está haciendo fetch de la web,
si combina las dos cosas, eso lo decidió e implementó Claude Code.

Como conté en otro post: las instrucciones las doy yo, la implementación la dejo.
Funciona y las respuestas que vuelven tienen pinta correcta, así que por ahora con eso me llega.
Si se rompe, le digo a Claude Code «arréglalo».

## Lo que no puede contestar se deriva al formulario

Que el bot conteste a todo es peligroso.

Consultas individuales sobre tallas concretas, envoltorio para regalo, pedidos B2B, incidencias.
Si dejas que el bot se moje en esto, luego hay desajustes.

Cuando el bot decide «esto mejor no lo contesto», lo deriva al formulario de contacto.
El diseño de los guardarraíles también lo dejé en manos de Claude Code.
Lo único que hice fue pedir, en una línea: «**lo que no se pueda contestar, que vaya al formulario de contacto**».

Qué preguntas contesta el bot y cuáles escala.
Esa frontera la trazó Claude Code.
Pienso revisar los logs de vez en cuando y ajustar si veo una clasificación claramente rara,
pero de momento no ha aparecido.

Si en 15 minutos estaba funcionando, fue porque dentro de esos 15 minutos había muy poco que pensar.

«Va abajo a la derecha», «basado en la API de Claude», «9 idiomas», «vuelve Render», «historial en Sheets»,
«lo que no puede contestar va al formulario».
Con eso decidido, el resto lo monta Claude Code.
Yo doy el GO y compruebo si funciona.

Al segundo día de tener la tienda abierta, ya estaba en marcha la base de automatización del soporte.
La primera de las «**una mejora al día**», fue esta.

Os sigo contando.

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
