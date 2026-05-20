<!-- canonical: https://moday.me/blogs/journal/first-inquiry-first-loss -->

# 24 horas después de abrir: las primeras consultas, y la primera venta que ya di por perdida

## Abrí el 18/5. El 19/5 llegaron dos correos.

Abrí la tienda el 18/5, tal como estaba previsto.

El post anterior lo cerré con eso de «abrir con el miedo todavía puesto». Al día siguiente de abrir, entraron dos correos.

El primero:

> Hi! Quick question — do you ship to Chicago, Dallas, San Jose
> or is your delivery limited to certain areas?
> Also, how long does it usually take for orders to arrive there?

El segundo:

> Can you deliver to Bavaria, Germany?

Voy a ser honesto: me dio un subidón importante.

Chicago, Dallas, San Jose, Baviera. Alguien cuyo nombre y cuya cara nunca voy a conocer había llegado hasta la tienda que monté yo, y se había interesado lo suficiente como para **decidir mandar un correo**. Esa clase de evidencia me cayó delante por primera vez.

## Abrí GA4. Estados Unidos estaba por encima de Japón.

En paralelo, miré GA4. La primera foto a 24 horas desde la apertura.

![Usuarios de GA4 por país](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/first-inquiry-first-loss-ga4-countries.png)

- United States: 22 users (44%)
- Japan: 14 users (28%)
- Germany: 6 users (12%)
- Singapore: 3 users
- Canada: 2 users
- South Korea: 1 user

El país en el que vivo, desde el que toqueteo la tienda todos los días, queda **por detrás de Estados Unidos**. Alemania, tercera.

Ese fue el momento en el que el geo-routing y el setup de nueve idiomas devolvieron algo a cambio — por primera vez, en números. En el post anterior escribí «no veo al cliente». La cara todavía no se enfoca. Pero la **geografía aproximada de dónde está** empieza a asomar.

Para que conste: pedidos siguen en cero. El interés es real, pero todavía no convierte. Algo falta — ansiedad sobre envíos, plazos, precio, el look. No sé cuál de ellos, y no lo voy a saber hasta que pueda observarlo. Ese es el punto en el que estoy ahora mismo.

## No pude contestar el mismo día.

Vuelvo a los correos.

Llegaron los dos. Lo agradezco. Pero **no fui capaz de contestar el mismo día en el que entraron**.

Los vi de noche, tarde, y esa noche tenía trabajo del curro principal corriendo. Redacté la respuesta en japonés, pasé las traducciones por Claude Code al inglés y al alemán, y los mensajes salieron, en realidad, **al día siguiente**.

La parte de redactar + traducir, una vez tienes el flujo montado, son cinco o diez minutos. Pero la latencia entre «entró el correo» y «estoy delante de la pantalla» ya añade retraso. Encima, para contestar a una pregunta sobre disponibilidad de envío hay que comprobar los países que cubre Gelato, estimar plazos — montar una respuesta seria pide un trozo de concentración.

En el correo como canal, contestar dentro de 24 horas no se considera mala educación. Pero la temperatura del otro lado se cae bastante en 24 horas.

La diferencia entre una tienda donde «mandas una pregunta y vuelve la respuesta rápido» y una donde «la respuesta vuelve al día siguiente» probablemente cambia la decisión de compra. Sobre todo cuando es una marca nueva, envía al extranjero, y el cliente ha pagado el coste de escribir en inglés.

Eso fue un **coste de oportunidad** claro. El primero.

## Así que ese mismo día metí un chatbot.

Después de mandar las respuestas tarde, me moví rápido.

**Las mismas preguntas van a volver.** Disponibilidad de envío, plazos, métodos de pago, tallaje. Contestarlas una a una por correo es demasiado lento como soporte.

Ese mismo día metí un widget de chat en la esquina inferior derecha de la tienda.

Está **montado directamente sobre la Claude API**, con soporte para nueve idiomas. Embebido en el tema de Shopify, responde en el locale del visitante de forma automática. Las respuestas de primera línea sobre envíos, plazos, tallas y pagos ya viven ahí.

Tiempo de construcción: **unos 15 minutos**. Le pedí a Claude Code, «mete un widget de chat abajo a la derecha, rutea los mensajes a través de la Claude API, ajusta el idioma al locale de Shopify del visitante» — y funcionó.

El estado de la tienda al final de ese día: **«si entra la misma pregunta otra vez, el cliente no espera 24 horas»**. Esa era la jugada disponible ese día.

## Arrancó el bucle de observación.

Hasta este punto, toda la fase de construcción funcionaba a base de «hipótesis que me había montado dentro de la cabeza».

La camiseta del día de la semana debería pegar con ingenieros y geeks. El internacional debería tener sentido. El modelo de nueve idiomas, multidivisa, sin inventario, debería funcionar. Todo era «debería».

Eso cambió en el momento en el que abrí.

GA4 empieza a devolver desgloses por país. Alguien manda una pregunta concreta por correo. Los logs del chat empiezan a acumular qué es lo que de verdad inquieta a los visitantes.

**El mundo ha empezado a contestar.**

Sigo sin tener «una forma de vender». El primer coste de oportunidad ya ocurrió. Pero como el bucle de observación está en marcha, **la siguiente jugada ya no es a ciegas**.

El principio real de una marca puede que no sea cuando la ingeniería está terminada, ni cuando la tienda abre — puede que sea cuando **el bucle de observación arranca a girar**, y esa es la parte que empezó hoy.

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
