<!-- canonical: https://moday.me/blogs/journal/how-i-use-claude-code -->

# Cómo uso Claude Code: no organizo, delego, y voy a lo que salga

## Toca mirar atrás y contar cómo uso Claude Code

He escrito bastante sobre la construcción de MODAY hasta aquí, pero todavía no había contado **cómo manejo Claude Code** por dentro.

La historia de cómo elegí el stack, cómo monté el pipeline de publicación, cómo localicé el blog a nueve idiomas, cómo metí un chatbot en 15 minutos — todo eso iba del lado de **qué construí**.

Ahora que la tienda ya está abierta y entrando en fase de operación, toca subirse un nivel y escribir la parte meta. Adelanto la conclusión: **no organizo, delego, y voy a lo que salga**.

Probablemente vaya en dirección contraria a la mayoría de las guías sobre Claude Code que circulan por ahí.

## El CLAUDE.md lo escribió Claude

Lo que se suele recomendar es: «**organiza la información del proyecto en CLAUDE.md**». Marca, stack técnico, convenciones de código, prioridades. Que el humano deje el contexto bien ordenado para que Claude Code pueda agarrarlo. Hasta ahí, el manual estándar.

El CLAUDE.md de MODAY **no tiene ni una línea escrita por mí**. Tampoco sé exactamente qué hay dentro.

Al principio del proyecto le dije a Claude Code «ordena tú mismo los archivos como te parezca», y empezó a recopilar por su cuenta la información de marca, el stack, la tabla de SKUs, la configuración de Markets y las prioridades por fase. Cuando lo miro por encima, está, seguramente, en un formato más legible para Claude del que yo conseguiría a mano.

De principio a fin, **no he hecho ni una tarea de organización**. Le he pasado a Claude la tarea de organizar en sí.

## Las sesiones las separo «a ojo»

Sí separo sesiones, pero **sin reglas**.

No tengo una división estricta por propósito. Las agrupo de manera bastante vaga: «creación de contenido», «mejoras de UI/UX», «MD (cosas variadas)». Dentro de la misma sesión mezclo generación de imágenes, traducción y código sin problema.

No las divido por rol (tipo «sesión de traducción», «sesión de código»). **Las divido por el flujo del trabajo**. Es una división sucia, pero el resultado es que los pensamientos se encadenan.

Estoy retocando una pantalla y se me ocurre «espera, si cambio esto, también convendría ajustar la traducción». Y lanzo la traducción ahí mismo, en la misma sesión. Como el coste de arrastrar contexto entre sesiones es cero, **no se me corta el hilo de las decisiones**. Eso, sorprendentemente, marca diferencia.

## Instrucciones técnicas, prácticamente ninguna

Ya lo conté en otro post: a la hora de elegir el stack, no di ni una condición técnica. Solo condiciones de negocio. Y al entrar en la implementación, la postura no cambió.

Lo único que sí transmito de forma consciente es:
«**Usa Shopify y Gelato de la manera estándar. Implementación a medida, lo mínimo**».

Lo considero una regla de oro del SaaS. Lo más estable a largo plazo es moverte dentro del rango que el proveedor anticipó. La custom mola a corto plazo, pero se rompe en cuanto el proveedor saca una actualización. Flujos estándar, API estándar, estructura de tema estándar. Solo se sale de ahí cuando es realmente necesario.

Con esa sola directriz, ya puedo dejar en manos de Claude Code casi todo: cómo llamar a la API, la estrategia de pruebas, el manejo de errores, los detalles de implementación.

## Cuando me pide aclaraciones, le contesto «hazlo tú»

Claude Code, a veces, viene a confirmar. «¿Me enseñas el contenido de este archivo?», «¿está bien así?», «¿cómo escribo el test?».

A casi todas esas preguntas le respondo «**hazlo tú**».

Si quiere ver un archivo, que use su propia herramienta. Si me pide una decisión, le devuelvo «decide tú». En la práctica, en casi todos los casos termina leyéndoselo, decidiendo por sí mismo, y llegando hasta la implementación sin más.

Esto es la versión práctica de lo que conté en otro post: «**quiero darle la iniciativa al lado de la IA**». No devolverle la decisión, dejársela.

Al final, lo único que queda en mi lado son **las cosas que no se pueden mover por API**. La cuenta bancaria, la revisión del proveedor de pagos, los alta de servicios, los datos de facturación, la emisión de claves API. Ahí los contratos son con humanos, así que ahí sí muevo yo las manos. El resto lo tiene Claude.

## Hago que Claude Code patrulle GA4 cada día y proponga mejoras

Esta es una rutina nueva, que empecé después de abrir.

Cada día Claude Code patrulla GA4 y **saca una lista de problemas y propuestas de mejora**. Yo le echo un ojo y descarto solo lo que claramente está mal enfocado. El 60–70 % restante lo manda a implementar ahí mismo.

Entre la propuesta y la implementación, lo único que hago es decir GO o NG. Escribir código, pensar el diseño — prácticamente cero.

Quiero convertir esto en el concepto operativo: «**implementar como mínimo una mejora al día**». Desde el momento en el que la tienda abrió, que cada día haya algo que sea un poquito mejor que ayer. Una marca cuyo bucle de mejora no se detiene, a largo plazo, termina ganando. Esa es la apuesta.

Y el 99 % de ese bucle de mejora lo mueve Claude Code.

## No organizo, y aun así está organizado

Llegado a este punto, lo pienso otra vez. No hago casi nada del «manual clásico de desarrollo»: organizar, diseñar, planificar.

No tengo un CLAUDE.md escrito por mí. Las sesiones van a ojo. El flujo de trabajo no está convertido en rutina. No hay un diseño técnico explícito, ni una herramienta de gestión de tareas. Y sin embargo, desde la construcción hasta la operación, la cosa rueda.

Para ser exactos: **la organización la he delegado en el lado de Claude**. Yo no la hago, pero Claude Code sí. Así que, como efecto secundario, el estado «organizado» se mantiene.

Esta estructura se parece bastante a cuando Masayoshi Son (el fundador de SoftBank) dice «hagámoslo» y un equipo de ejecución súper competente arranca y se encarga de organizar e implementar todo. **Yo me quedo en el lado de «hagámoslo», y el equipo de ejecución es la IA**.

En la era de la IA, una persona sola puede reproducir esa estructura. Esa es, de lejos, la mayor sensación que me llevo de estas tres semanas.

## Cierre

No creo que esta sea la forma correcta. Seguro que también funciona el enfoque clásico — escribir bien el CLAUDE.md, separar las sesiones por propósito, convertir el flujo en rutina.

Pero en mi caso, **iba más rápido no organizando**. Si tengo un rato libre para dedicarlo a organizar, prefiero usarlo en lanzarle algo a Claude Code y decidir sobre lo que devuelva.

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
