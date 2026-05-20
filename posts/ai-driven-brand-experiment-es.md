<!-- canonical: https://moday.me/blogs/journal/ai-driven-brand-experiment -->

# Cuatro cosas que ni la IA puede quitarme

Estoy construyendo MODAY — una marca de camisetas día-de-la-semana operada por una sola persona — y estoy intentando pasarle absolutamente todo a la IA. Tres días después, cuatro cosas se negaron a moverse.

## Por qué hago esto, en realidad

La mitad evidente del porqué ya está contada en otro post: una camiseta japonesa con la palabra «lo siento» impresa que se hizo viral, y los días de la semana borrándose unos contra otros en remoto. Esa es la superficie.

La otra mitad cuesta más decirla en voz alta — quiero entender cómo se construyen empresas en la era de la IA, y quiero entenderlo antes de que lo hagan los demás.

Mi trabajo principal es consultoría de e-commerce. Veo bastantes operaciones por dentro. Por eso, cuando la IA generativa explotó hace un par de años, hubo una pregunta que se instaló y no se fue: ¿hasta dónde se puede dejar que una IA opere realmente un negocio?

Leer no responde a eso. Twitter no responde a eso. Los papers tampoco. La pregunta no se rinde ante la lectura — se rinde ante un negocio real con dinero real moviéndose por dentro.

Así que MODAY es una marca, sí. Pero también es un experimento de una sola persona, hecho en la escala adecuada para poder medir. Cero inventario. Operador solo. Global desde el día uno. Tres días hasta el lanzamiento. Dinero real, clientes reales, paquetes reales. En proyectos de hobby o pilotos internos el criterio se ablanda. Sin tener algo en juego, no se mide nada.

La regla: nada de líneas. Pasárselo todo. Ver qué no se mueve.

## Tres días dentro, cero arrepentimientos

Aún no he tenido el momento de «esto no debí haberlo dejado a la IA». No con la selección del stack. No con el diseño. Ni con la tienda, los webhooks, las traducciones, el copy. He enviado a producción lo que Claude generó, casi tal cual, en todo el build.

Suena a presumir. No lo es. La lectura honesta es más oscura — también le he pasado a Claude mis propios criterios de juicio. Ya no queda nada en mí de lo que poder arrepentirse. Si hubiera conservado mis propias opiniones, antes o después llegaría el momento de «un momento, yo habría ido por otro lado». Ese momento no ha llegado.

Para bien y para mal.

## Y sin embargo — cuatro cosas se quedaron

Por más que dije «nada de líneas», cuatro partes de este build se negaron a delegarse. Por sustracción, ahí van.

**1. La decisión de mandar un prompt, siquiera.**

La primera frase que tecleo a Claude — «¿qué hacemos ahora?» — sigue saliendo de mí. Todas las veces. No consigo eliminarla.

Cuando consiga delegar también eso, estaré en el siguiente nivel. Todavía no.

**2. Cuenta bancaria y aprobación de pagos.**

KYC de Shopify Payments. Verificación de identidad de Stripe. Cuentas para recibir pagos internacionales. Aquí no entra nada que no sea un humano. Te presentas con el documento, firmas con tu nombre y tu cara, y te conviertes en la parte del contrato.

**3. Altas en servicios y registrar la tarjeta.**

Gelato. Render. fal.ai. Make.com. Anthropic. En cada uno creo la cuenta, meto la tarjeta y pulso «pasar a plan de pago». Cada alta es mi mano en el panel.

**4. Generar la API key — hasta el momento de entregársela.**

Para que Claude Code pueda llamar a una API, la clave tiene que existir. El botón «crear nueva clave» lo pulso yo. En cuanto la clave entra en el `.env`, deja de ser mía.

Esa es la lista completa. En tres días, esos son los únicos puntos en los que mi mano se ha movido físicamente. Todo lo demás lo opera Claude.

## El número 1 también lo quiero soltar

De los cuatro, el que más quiero quitarme es el primero — la decisión de prompt-ear.

La versión a la que apunto: Claude Code aparece con «la siguiente cosa es esta», yo respondo solo sí o no, y la dirección del negocio en sí migra al lado de la IA.

Técnicamente esto seguramente ya se puede. Con un setup tipo agente, Claude Code descompone sus propias tareas, las implementa y propone la siguiente, en bucle. Hay gente corriendo versiones de esto ya hoy.

En el estado actual de MODAY no he ido tan lejos. Una parte de mí todavía quiere escoger personalmente la dirección del primer paso. Siendo honesto, ese es justo el tema. Soltarlo es mi siguiente movimiento.

## Las otras tres no son el límite de la IA — son el del sistema

Esta es la frase que más quería escribir.

El banco, el KYC, las altas, las API keys — ninguna de estas se quedó conmigo porque «a la IA le falte criterio». No es por eso.

El motivo real es institucional. La IA no tiene personalidad jurídica. Ni como persona física, ni como persona jurídica. No puede ser parte de un contrato. Eso es todo.

Técnicamente, a Claude Code con automatización de navegador probablemente podría pedirle mañana que hiciera todo esto. Rellenar el formulario. Subir la foto del documento. Pulsar el enlace del correo de verificación. Computer Use ya existe. El bloqueo no es de capacidad.

El bloqueo es que, aunque Claude hiciera los clics, **la parte registrada seguiría siendo yo.** Claude solo estaría rellenando formularios bajo mi nombre. La responsabilidad se queda con el humano.

Por tanto, esas tres no son donde la IA toca su límite. Son los puntos donde las instituciones de la sociedad aún no han llegado. El día en que una IA pueda ser legalmente operadora de un negocio, esas tres también migrarán.

## Sustracción, no segregación

El marco de «esto lo hace el humano, esto lo hace la IA» va a parecer obsoleto dentro de tres años.

En el momento en que dibujas la línea — «humanos aquí, IA allí» — la línea se convierte en una restricción. Y la pregunta «¿hasta dónde puede llegar la IA?» se vuelve incontestable desde dentro de esa restricción. No puedes medir el límite si has definido el límite por adelantado.

Por eso MODAY no es segregación. Es un intento de pasárselo todo a la IA y comprobar, por sustracción, qué no se ha movido.

Cuatro cosas se quedaron. Tres son institucionales. Una es mi propio impulso.

El tiempo resuelve las tres. La una — esa la tengo que soltar yo.

Hasta la próxima.

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
