# Brief de proyecto — Lenguajes Digitales 5
### Plataforma de mascotas — Colombia

**Autores:** Samuel Parada y Andrés Claros
**Versión:** 3 — ajustada con retroalimentación de sesión (ronda 2)

---

## 1. Contexto o problema

La información de una mascota no deja de producirse: cada consulta, vacuna, desparasitación, examen, tratamiento, cambio de alimentación, variación de peso o de comportamiento genera un dato nuevo. El problema no es que esa información no exista, sino que nunca termina de juntarse: queda archivada donde se generó —la carpeta de una clínica, el carnet físico, un chat de WhatsApp con el veterinario, la memoria del dueño— y cada pieza vive aislada de las demás, sin que nadie la conecte con el resto.

Esa fragmentación no es solo un problema de organización personal; tiene una raíz estructural. En Colombia, la Ley 576 de 2000 obliga a que toda historia clínica veterinaria quede consignada y establece que solo puede conocerla un tercero con autorización del propietario — pero, a diferencia de la salud humana, no existe una reglamentación de formato y manejo que obligue a que esa información sea portable o quede centralizada en algún punto. El resultado directo es que cada proveedor la lleva a su manera, en su propio sistema o cuaderno, y el dueño nunca termina con una versión completa y propia de la información de su mascota.

Esa brecha —entre la información que existe y la que el dueño realmente tiene a la mano— es la que se siente en el día a día, no en un caso excepcional: el dueño no puede responder con precisión qué vacuna le pusieron y cuándo, qué medicamento le cayó mal, cuánto pesaba hace seis meses o qué decía el examen del año pasado — ni en un control de rutina, ni cuando cambia de veterinaria, ni cuando lo deja en una guardería, ni cuando viaja, ni cuando lo atienden de urgencia. Y cada vez que esa información hace falta, hay que reconstruirla desde cero: en el camino se repiten exámenes, se gasta tiempo de consulta y se termina decidiendo con datos incompletos. Quien más lo sufre es el dueño; el veterinario queda en segundo lugar, al atender sin contexto.

> **"¿Cómo hago para tener toda la información de mi mascota en un solo lugar, lista para mostrar en cualquier consulta, viaje o guardería?"**

Esa es la pregunta que hoy no tiene respuesta, y es la que conecta el problema con lo que vamos a construir.

Los temas de identificación y logística (viajes, hoteles, autorización de procedimientos) quedan como un problema secundario a explorar más adelante.

---

## 2. Objetivo del producto

Que cada mascota tenga un perfil digital único, que le pertenece a su dueño, se mantenga actualizado sin esfuerzo y se pueda consultar o mostrar en segundos, en cualquier momento y con quien haga falta — no como un historial clínico que solo importa dentro del consultorio, sino como el punto de referencia al que se recurre cada vez que alguien necesita saber algo de la mascota: una cita de rutina, un cambio de veterinaria, una guardería, un viaje, una urgencia, o la pregunta que le hace un familiar que se queda cuidándola el fin de semana. El dueño gana control y deja de reconstruir información; quien recibe a la mascota por primera vez puede atenderla con contexto completo.

En el uso diario, esto se ve así: el dueño registra cada evento apenas ocurre —una vacuna recién puesta, el resultado de un examen, un cambio de alimentación, una observación de comportamiento— con el soporte correspondiente (foto del carnet, del examen o de la fórmula) y unos pocos campos asociados; es el propio dueño quien registra el resultado de cada consulta veterinaria, con lo que el veterinario no necesita cuenta ni acceso de edición. Del otro lado, cuando la información se necesita, el dueño abre el perfil de su mascota desde el celular y encuentra primero una vista rápida de lo que más se pregunta —identificación, alergias, medicación vigente, últimas vacunas, peso— y, un nivel más abajo, el detalle completo si hace falta profundizar. Mostrar esa información a alguien más —un veterinario nuevo, un cuidador, el personal de una guardería— no exige que esa persona tenga cuenta ni use la misma aplicación.

**"Que la salud de tu mascota nunca dependa de dónde quedó el papel."**

---

## 3. Oportunidad de negocio

**Tamaño y dinámica del mercado.** La tenencia de mascotas en Colombia pasó de 48 % de los hogares en 2020 a un rango de 60 %–67 % en 2025, según la investigación anual del Pet Food Institute; el DANE y mediciones independientes como Kantar reportan cifras en ese mismo rango o superiores [1]. El gasto en productos y servicios para animales de compañía llegaría a **$6,1 billones de pesos en 2026**, según proyecciones de Euromonitor International [2], tras crecer cerca de 85 % en cinco años [3]. Dentro de ese gasto, la salud es el rubro que más se está encareciendo: en el año terminado en febrero de 2026 los servicios veterinarios y de cuidado subieron 9,72 %, frente a 5,29 % de la canasta familiar total, según el DANE [4].

**Público objetivo acotado.** No apuntamos a "los dueños de mascotas en Colombia". El segmento inicial es:

> Dueños de **perro o gato** en **Bogotá**, adultos entre 25 y 45 años de hogares urbanos de ingreso medio y medio-alto, que llevaron a su mascota a **por lo menos una consulta veterinaria particular en el último año** y que han pasado por **más de un proveedor** (clínica, especialista, guardería, peluquería, urgencias).

Es el segmento que efectivamente genera información clínica, ya vive la fragmentación en carne propia y es alcanzable para entrevistar y testear directamente. Estimación razonada de su tamaño, con los supuestos a la vista: Bogotá tiene alrededor de 2,8 millones de hogares (Censo DANE 2018); la tenencia reportada para la ciudad va de 40 % en la Encuesta Multipropósito 2021 del DANE a 65 % en la medición de Cifras y Conceptos de 2024 [5], lo que da un rango de **1,1 a 1,8 millones de hogares con mascota**. Si asumimos que una cuarta parte cumple el perfil completo (perro o gato + consulta particular reciente + más de un proveedor), el mercado inicial queda en el orden de **300.000 a 450.000 hogares**. *Supuesto por validar: la proporción de 1 de cada 4 es una estimación propia, no un dato de fuente.*

**Buyer persona.** Para tangibilizar ese segmento con una persona concreta:

> **Valentina, 34 años — Chapinero, Bogotá.**
> Trabaja en un cargo profesional de tiempo completo, vive con su pareja y tiene un perro y un gato. Los lleva a controles de rutina en una clínica veterinaria de barrio, pero en el último año tuvo que recurrir además a una clínica de urgencias distinta y a una guardería cuando viajó.
>
> **Cómo maneja la información hoy:** guarda las fotos de los carnets de vacunación en el rollo de su celular, mezcladas con fotos personales; el historial de exámenes vive en PDFs sueltos que le mandan por WhatsApp distintas clínicas; y para lo que no encuentra, llama a la primera veterinaria a preguntar, cuando alguien se lo recuerda.
>
> **Su dolor principal:** en la última urgencia de su perro, la clínica le preguntó si tenía alguna alergia registrada y no supo responder con certeza. En otra ocasión pagó un examen de sangre que, según le dijeron después, ya se lo habían hecho meses antes en otro lugar.
>
> **Qué la haría probar la plataforma:** que registrar un evento le tome menos de un minuto —si es más complicado que tomar una foto y guardarla, no lo va a sostener— y que, la próxima vez que la llamen de una clínica nueva o de la guardería, pueda resolver la pregunta mostrando el perfil desde su celular en vez de tratar de recordar.
>
> **Su objeción probable:** "¿y si dejo de usarla, pierdo la información de años de mis mascotas?" — la confianza en que su información queda segura y disponible es una condición para que se registre en primer lugar.

**De dónde sale el ingreso.** El producto se ofrece como una única versión, pagada por el dueño mediante suscripción: perfil completo por mascota, historial con archivos adjuntos, múltiples mascotas, generación de reportes para compartir y alertas de vacunas y controles. No hay una versión gratuita limitada ni un segundo nivel de pago — todo dueño que se registra accede desde el inicio a la misma funcionalidad completa, lo que simplifica la decisión de compra y evita fragmentar la base de datos entre usuarios con información parcial y usuarios con información completa.

**Cómo escala.** Con una base de dueños activos, el modelo se extiende a las veterinarias, mediante un plan por clínica para recibir y actualizar perfiles con autorización del dueño: menos tiempo de consulta gastado en reconstruir antecedentes y más retención de clientes. Las aseguradoras entran solo después y con un rol acotado y explícito: verificar información al momento de suscribir una póliza o de sustentar una reclamación, siempre con datos que el dueño autoriza. No hacen parte del alcance inicial del producto.

---

## 4. Hipótesis

Creemos que los dueños de perros y gatos que ya asisten a consulta veterinaria particular van a registrar a su mascota y a mantener su perfil actualizado si la plataforma les permite consultar y mostrar esa información en el momento exacto en que se la piden, porque hoy asumen un costo concreto cada vez que no la tienen: exámenes que se repiten, consultas más largas y decisiones clínicas tomadas con datos incompletos.

**Qué tendríamos que ver para confirmarla:** que una proporción significativa de los dueños contactados complete el registro de al menos una mascota con tres o más datos clínicos (adquisición y registro); que vuelvan a abrir o actualizar el perfil en las dos semanas siguientes sin que se lo pidamos (retención); y que, en una situación real —una cita, un cambio de proveedor, un viaje, una guardería— usen efectivamente el perfil para mostrar la información de su mascota, en vez de quedarse solo con el registro inicial.

**Qué la descartaría:** que registren a la mascota una vez y no vuelvan; o que consideren la necesidad ya resuelta con lo que usan hoy (fotos en el celular, carpeta física, preguntarle a la clínica) y no le atribuyan ningún costo a esa forma de hacerlo.

**Datos que faltan (Discovery):** cuántos dueños cambiaron de veterinaria o de proveedor en el último año; cuántos llevan hoy algún registro propio y en qué formato; con qué frecuencia les han pedido información que no tenían a mano; y cuánto tiempo o dinero les ha costado no tenerla.

---

## 5. Value prop principal y secundaria

**Principal:**

> Para el dueño de un perro o un gato que reparte el cuidado de su mascota entre varios proveedores, la plataforma reúne toda su información en **un perfil único que él controla y puede mostrar en segundos** —en la consulta, en la guardería, en un viaje o donde se la pidan—, a diferencia de reconstruirla cada vez a punta de carnets, carpetas, chats y memoria.

Beneficios tangibles para el dueño: menos exámenes repetidos y el gasto que traen; menos minutos de consulta gastados en reconstruir antecedentes; menor riesgo por alergias no informadas o dosis calculadas sin historial; y un solo lugar al que volver cuando cambia de veterinaria, viaja o deja la mascota al cuidado de alguien más.

**Secundaria:**

> Para el veterinario, el cuidador o la guardería que reciben a la mascota por primera vez, el perfil llega ordenado y con soportes, de modo que la atención arranca con contexto en lugar de con un interrogatorio.

Refuerza la decisión del dueño —le da sentido a compartir el perfil y hace que la información valga más—, pero el producto se sostiene aunque ninguna clínica lo adopte, porque el valor central es del dueño.

---

## 6. Qué vamos a hacer

Vamos a construir una plataforma digital (web/app móvil) centrada en una capacidad núcleo: el **perfil completo de la mascota**, donde se guarda y muestra toda su información —historial médico, alimentación, comportamiento, identificación, entre otros—, con fácil acceso para quien la necesite en el momento (el dueño, un veterinario, un cuidador).

Lo que hay que construir y probar este semestre para validar la hipótesis se concreta en cuatro mecanismos:

- **Perfil con línea de tiempo:** vacunas, desparasitaciones, consultas, exámenes, tratamientos, peso, alimentación y comportamiento, cada uno con su soporte adjunto (foto del carnet, PDF del examen, fórmula médica). Es el dueño quien registra cada evento, incluido el resultado de sus consultas veterinarias, con una foto del documento que le entrega el veterinario — este último no necesita cuenta ni acceso de edición.
- **Vista de acceso rápido:** identificación, alergias, medicación vigente, últimas vacunas y peso — lo primero que preguntan, sin tener que buscar.
- **Compartir mediante un reporte en PDF:** el dueño genera, desde el perfil de su mascota, un reporte en PDF con la información relevante —completa o filtrada a lo que necesite mostrar en ese momento— y lo comparte por el medio que prefiera (WhatsApp, correo, impreso), sin que quien lo reciba necesite cuenta ni la misma aplicación. Es la forma más simple de resolver el "mostrar la información ya" sin depender de infraestructura de permisos ni de vencimientos automáticos, que queda para una iteración posterior.
- **Identificador como dato del perfil:** el dueño escribe a mano el número de su microchip o el código de su placa, como un campo más del perfil — sin lectura automática ni vinculación entre sistemas.

La versión mínima que demuestra la propuesta de valor es: el dueño registra a su mascota y su información en la plataforma, anota el identificador que ya tenga (microchip o placa), y puede generar y compartir el PDF de ese perfil completo con quien lo necesite —de forma inmediata— en una consulta o emergencia.

**Visión de producto a futuro**, fuera de lo que se construye y valida este semestre: lectura automática de microchips y códigos QR, vinculación entre los distintos sistemas de identificación existentes, una conexión directa entre la aplicación del dueño y los sistemas de gestión de las veterinarias que permita enviar o sincronizar el perfil sin pasar por el PDF intermedio, y la cédula animal de la Red Colombiana de Identificación Animal (RCIA) si esta se aprueba y entra en operación —ninguna de estas existe todavía como sistema oficial u operativo, así que no forman parte de lo que hay que probar para validar la hipótesis.

Queda fuera de alcance para este semestre: avatar 3D, recordatorios genéricos, IA genérica, emisión de un identificador propio (microchip o cédula), permisos granulares y vencimiento automático al compartir, y otras funciones ya comoditizadas por el software veterinario existente.

---

## Fuentes

1. Pet Food Institute, investigación anual sobre tenencia de mascotas en Colombia (2025), reseñada por *El Espectador* — tenencia entre 60 % y 67 % en 2025 frente a 48 % en 2020; Kantar (2024) reporta 70 % en hogares encuestados. https://www.elespectador.com/la-red-zoocial/hasta-el-67-de-los-hogares-en-colombia-tienen-una-mascota-segun-reciente-estudio/
2. Euromonitor International, proyección de gasto en mascotas en Colombia para 2026, citada por *El Colombiano* e *Infobae*. https://www.elcolombiano.com/negocios/dos-de-cada-tres-hogares-colombianos-tienen-mascota-cuanto-gastan-y-ahorran-HO29411402
3. Bancolombia, crecimiento del sector de productos y servicios para mascotas en los últimos cinco años, citado por *Pet Industry*. https://petindustry.co/gerencia/del-dink-al-mercado-colombiano-como-el-consumidor-pet-de-ee-uu-anticipa-la-industria-de-mascotas-en-colombia-hacia-2026/
4. DANE, variación anual de precios a febrero de 2026 — servicios veterinarios y de cuidado (9,72 %) frente a la canasta familiar total (5,29 %), reportado por *Semana*. https://www.semana.com/economia/macroeconomia/articulo/perros-y-gatos-cada-vez-mas-costosos-el-gasto-en-salud-de-las-mascotas-crece-por-encima-de-la-inflacion/202621/
5. DANE, Encuesta Multipropósito 2021 (cerca de 4 de cada 10 hogares de la cabecera de Bogotá con al menos una mascota) y Cifras y Conceptos, encuesta Polimétrica 2024 (65 % en Bogotá), ambas reseñadas por *El Espectador*. https://www.elespectador.com/la-red-zoocial/revelan-el-numero-de-mascotas-que-hay-en-colombia-son-mas-perros-que-gatos-noticias-hoy/
6. Ley 576 de 2000, artículo 61 — Código de Ética para el ejercicio de la medicina veterinaria en Colombia: la historia clínica es de consignación obligatoria y la información es privada, sometida a reserva, y solo puede ser conocida por terceros con autorización del propietario. La ausencia de una reglamentación técnica equivalente a la Resolución 1995 de 1999 (historia clínica humana) está documentada en investigación académica sobre historia clínica y consentimiento informado en medicina veterinaria en Colombia.

---

*Documento vivo: se actualiza a medida que avanza la investigación y el desarrollo del producto.*
