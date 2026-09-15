# Discovery — supuestos a validar con entrevistas reales

> **Estado:** guía lista para usar. Todavía no se ha hecho ninguna entrevista.
> **Base:** [brief-corte1.md](brief-corte1.md) — §1 problema, §3 Valentina y modelo de ingresos, §4 hipótesis y datos que faltan, §5 propuesta de valor.

---

## 1. Para qué sirve

El brief se apoya en supuestos razonables que todavía no están comprobados. Esta guía los convierte en preguntas para hablar con dueños y con quienes reciben a sus mascotas, **antes** de invertir más tiempo construyendo sobre ellos.

Lo que salga de aquí alimenta [flujo-pantallas.md](flujo-pantallas.md), ajusta [design-system.md](design-system.md) y, si hace falta, cambia las specs de las features.

## 2. Supuestos clave

Ordenados por riesgo: los de arriba, si resultan falsos, cambian el producto.

| ID | Supuesto | Si resulta falso… | Brief | Prioridad |
|---|---|---|---|---|
| **S1** | Los dueños del segmento **registrarían ellos mismos** cada evento, si les toma menos de un minuto | El perfil queda vacío. Todo el producto depende de este comportamiento | §2, §3, §6 | 🔴 Alta |
| **S2** | Lo que usan hoy (fotos en el rollo, carpeta, PDFs sueltos en WhatsApp, llamar a la clínica) **no les resuelve** | La necesidad ya está resuelta: es justo lo que descarta la hipótesis | §4 | 🔴 Alta |
| **S3** | En el último año **les han pedido información que no tenían a mano** (consulta, urgencia, guardería, viaje) | No hay un problema frecuente que resolver | §1, §4 | 🔴 Alta |
| **S4** | No tenerla **les costó algo concreto**: un examen repetido, una consulta más larga, una decisión con datos incompletos | El problema existe pero no duele lo suficiente para cambiar un hábito | §1, §4 | 🔴 Alta |
| **S5** | **Mostrar el perfil en el celular o enviar un PDF** resuelve lo que necesita quien recibe a la mascota | El mecanismo de compartir no sirve en la situación real | §4, §5, §6 | 🟠 Media |
| **S6** | Quien recibe **confía** en información registrada por el dueño, si trae la foto del soporte y la fecha | El veterinario repite todo igual y la propuesta secundaria se cae | §5 | 🟠 Media |
| **S7** | Lo primero que preguntan es **identificación, alergias, medicación vigente, últimas vacunas y peso** | La vista rápida muestra lo que no es | §2, §6 | 🟠 Media |
| **S8** | La información está **repartida entre varios proveedores**: el dueño pasó por más de uno en el último año | La clínica de siempre ya funciona como "lugar único" | §3, §4 | 🟠 Media |
| **S9** | El **miedo a perder la información** frena el registro (la objeción de Valentina) | Se sobreinvierte en respaldo, o se subestima la barrera principal | §3 | 🟡 Baja |
| **S10** | Un dueño del segmento **pagaría una suscripción** por esto | El modelo de ingresos no se sostiene. No bloquea el semestre, pero hay que empezar a saberlo | §3 | 🟡 Exploratoria |

## 3. A quién entrevistar

### Dueños — entre 6 y 8 personas

Que cumplan el segmento del brief. Antes de agendar, verificar con este filtro:

1. ¿Tienes perro o gato? → **sí**
2. ¿Vives en Bogotá? → **sí**
3. ¿Qué edad tienes? → **entre 25 y 45**
4. En el último año, ¿llevaste a tu mascota a una consulta veterinaria particular? → **sí**
5. En el último año, ¿en cuántos lugares distintos la han atendido o cuidado (clínica, especialista, urgencias, guardería, peluquería)? → **dos o más**

Quien no cumpla el punto 5 igual puede servir como contraste, pero máximo una entrevista de ese tipo, anotada aparte.

### Quienes reciben a la mascota — 2 o 3 personas

Un veterinario de clínica particular, alguien de una guardería o un paseador y, si se consigue, alguien de urgencias. Validan S5, S6 y S7 desde el otro lado del mostrador.

### Dónde encontrarlos

Grupos de Facebook y WhatsApp de mascotas en Bogotá, parques con zona canina, clínicas y guarderías de barrio, conocidos de conocidos. **Eviten a amigos cercanos y a la familia:** por cariño, dicen lo que uno quiere oír.

Mensaje de contacto (no menciona la aplicación, para no sesgar la conversación):

> Hola, somos Samuel y Andrés, estudiantes de la Universidad El Bosque. Estamos investigando cómo los dueños de perros y gatos manejan la información de salud de sus mascotas. ¿Nos regalas 30 minutos para conversar? No vendemos nada.

## 4. Reglas de la entrevista

1. **Preguntar por el pasado concreto, no por el futuro hipotético.** Lo que alguien hizo es evidencia; lo que dice que haría, no.
2. **No presentar la idea.** En cuanto se habla de la aplicación, la persona empieza a ser amable en lugar de honesta.
3. **Pedir que muestren.** "¿Me muestras dónde tienes el carnet?" vale más que "¿dónde lo guardas?".
4. **Escuchar el 80 % del tiempo.** Los silencios incómodos traen las mejores respuestas.
5. **Anotar citas textuales**, con las palabras exactas de la persona.
6. **Uno pregunta y el otro anota.**

| ❌ No preguntar | ✅ Preguntar |
|---|---|
| ¿Usarías una app para guardar la historia de tu mascota? | Cuéntame la última vez que te pidieron un dato de tu mascota. ¿Qué hiciste? |
| ¿Te parece útil tener todo en un solo lugar? | ¿Me muestras dónde tienes el último examen? |
| ¿Registrarías cada vacuna en una app? | ¿Alguna vez anotaste algo de tu mascota por tu cuenta? ¿Lo seguiste haciendo? |
| ¿Pagarías una suscripción por esto? | Además de las consultas, ¿qué pagas hoy relacionado con tu mascota? |
| ¿No es un problema no tener la información? | ¿Y qué pasó después? |

## 5. Guion para dueños (30 a 35 minutos)

### Apertura — 2 min

- Presentarse: "No hay respuestas correctas. Nos sirve más lo que te ha pasado de verdad que lo que creas que queremos oír".
- **Autorización** (Ley 1581 de 2012): "¿Nos autorizas a grabar el audio, solo para tomar notas? No publicamos tu nombre: en el informe usamos un seudónimo". Si no autoriza, solo notas escritas.

### Contexto — 5 min · *S8*

- Cuéntame de tu mascota (o de tus mascotas): cómo se llama, qué edad tiene.
- ¿A dónde la llevas cuando necesita algo? ¿Siempre al mismo lugar?
- En el último año, ¿por qué lugares ha pasado? (clínica, urgencias, especialista, guardería, peluquería)
- ¿Quién más la cuida cuando tú no puedes?

### La última vez — 10 min · *S3, S4, S7*

El corazón de la entrevista. Ir a un episodio concreto y quedarse ahí.

- Cuéntame la última vez que alguien te preguntó algo de la salud de tu mascota: una vacuna, un medicamento, un examen, el peso. ¿Quién te preguntó? ¿Dónde estabas?
- ¿Qué fue lo primero que te preguntó? *(S7)*
- ¿Supiste responder? ¿Cómo lo averiguaste? ¿Cuánto te tomó?
- ¿Qué pasó después? ¿Hubo que repetir algo, pagar algo o esperar? *(S4)*
- ¿Te ha pasado en una urgencia? ¿Y al cambiar de veterinaria?

### Cómo guarda la información hoy — 8 min · *S2, S1, S9*

Pedir que la muestre y cronometrar en silencio.

- ¿Me muestras dónde tienes el carnet de vacunas? *(Anotar dónde estaba, cuánto tardó en encontrarlo y en qué estado está.)*
- ¿Y el último examen que le hicieron?
- ¿Alguna vez anotaste algo por tu cuenta —peso, comida, medicamentos—? ¿Dónde? ¿Lo seguiste haciendo? ¿Por qué lo dejaste? *(S1: la señal más importante de toda la entrevista.)*
- ¿Alguna vez perdiste información de tu mascota (cambio de celular, clínica que cerró, papel perdido)? ¿Qué hiciste? *(S9)*

### Mostrarle a otros — 5 min · *S5, S6*

- La última vez que dejaste a tu mascota con alguien (guardería, familiar, viaje), ¿qué información le diste? ¿Cómo se la diste?
- ¿Te pidieron algún documento? ¿En qué formato lo entregaste?
- Cuando le contaste algo a un veterinario nuevo, ¿te pidió algún soporte o te creyó?

### Gasto — 3 min · *S10*

- Además de las consultas, ¿qué pagas hoy relacionado con tu mascota? ¿Algún plan de salud, seguro o aplicación?
- ¿Pagas alguna suscripción digital? ¿Cuál no cancelarías nunca, y por qué?

### Cierre — 2 min

- ¿Hay algo de este tema que no te pregunté y debería haberte preguntado?
- ¿Conoces a alguien con mascota que haya pasado por varias veterinarias?
- ¿Podemos escribirte en unas semanas para que pruebes algo que estamos construyendo?

## 6. Guion para quienes reciben a la mascota (15 a 20 minutos)

- Cuando llega una mascota que no conoces, ¿qué es lo primero que preguntas? ¿En qué orden? *(S7)*
- Cuéntame la última vez que atendiste o recibiste una mascota sin información previa. ¿Qué hiciste? ¿Hubo que repetir algo? *(S4)*
- ¿Cómo te llega hoy la información que viene de otros lugares? ¿Papel, WhatsApp, nada? *(S5)*
- ¿Alguna vez un dueño te llevó sus documentos organizados o un resumen? ¿Qué hiciste con eso? *(S5, S6)*
- ¿Qué hace que confíes en lo que te cuenta un dueño? ¿Qué te hace dudar? *(S6)*
- *(Guarderías y paseadores)* ¿Qué exiges al recibir una mascota? ¿Cómo lo verificas?

## 7. Después de cada entrevista

En las 24 horas siguientes, llenar una ficha **con seudónimo y sin datos personales**: teléfonos, cédulas y direcciones no van al repositorio, y los audios tampoco.

```markdown
### Entrevista 01 — "Carolina" (seudónimo)
- Fecha · duración · quién entrevistó · presencial o virtual
- Perfil: especie(s) · localidad · rango de edad · lugares en el último año
- Episodio más reciente, con detalle:
- Cómo guarda la información hoy (lo que vimos, no lo que dijo):
- Costos concretos que mencionó:
- Citas textuales:
- Evidencia: S1 ✔/✘/— · S2 … · S10
- Lo que no esperábamos:
```

Las fichas pueden ir al final de este archivo o en `docs/entrevistas/`, una por archivo.

## 8. Cómo decidir

### Criterios fijados antes de entrevistar

Se escriben **antes** de la primera entrevista, para no acomodar después la lectura a lo que se quería oír. Son una propuesta: ajústenlos entre los dos, pero antes de empezar. Están calculados sobre 8 dueños y 3 receptores; si entrevistan menos, conserven la proporción.

| Supuesto | Se sostiene si… | Se cae si… |
|---|---|---|
| S1 | 3 o más dueños han llevado algún registro propio en algún momento | Nadie ha registrado nunca nada por su cuenta |
| S2 | 4 o más tardan más de 2 minutos en encontrar el carnet o el último examen, o no lo encuentran | La mayoría lo encuentra en segundos y no le ve problema |
| S3 | 5 o más relatan un episodio concreto de los últimos 12 meses | Los episodios son raros o de hace años |
| S4 | 3 o más mencionan un costo concreto: examen repetido, pago extra, demora | Nadie asocia un costo a no tener la información |
| S5 | Los receptores describen un formato que les sirve y se parece a un documento ordenado | Los receptores prefieren siempre llamar a la clínica anterior |
| S6 | Los receptores aceptan la información del dueño cuando trae soporte y fecha | Repiten todo igual, venga como venga |
| S7 | 2 o más de 3 receptores preguntan primero por esos datos | Aparecen otros datos más importantes (por ejemplo, cirugías o enfermedades crónicas) |
| S8 | 5 o más pasaron por dos o más lugares | La mayoría usa un solo lugar para todo |
| S9 | 3 o más perdieron información alguna vez, o mencionan el miedo sin que se les pregunte | Nadie lo menciona |
| S10 | 3 o más mantienen alguna suscripción relacionada con cuidado o bienestar | *(Exploratorio: solo informa, no descarta)* |

### Síntesis

Al terminar todas las entrevistas, armar una matriz: filas = supuestos, columnas = entrevistas, celdas = ✔ a favor, ✘ en contra, — sin evidencia. Debajo de cada fila, las dos o tres citas que mejor la representen.

### Qué hacer con los resultados

| Resultado | Acción |
|---|---|
| S1 se cae | Replantear el registro antes de construir más: por ejemplo, primero solo la foto y los datos después. Ajustar la spec 001 y volver a correr `/speckit-plan` y `/speckit-tasks` |
| S2, S3 o S4 se caen | La hipótesis está en riesgo: actualizar el brief antes de seguir construyendo |
| S5 o S6 se caen | Rediseñar el reporte PDF (feature 003) con lo que sí piden los receptores |
| S7 cambia | Ajustar la vista rápida (feature 002) y el resumen del PDF |
| Hallazgos sobre recorridos y pantallas | Llevarlos a [flujo-pantallas.md](flujo-pantallas.md) |
| Hallazgos sobre vocabulario o legibilidad | Ajustar [design-system.md](design-system.md) |

## 9. Después: validar la hipótesis con el producto

Las entrevistas validan el problema. La hipótesis del brief (§4) se confirma **con el producto en uso**, observando tres señales:

| Señal | Qué hay que ver | Cómo medirla mientras los datos vivan en el navegador |
|---|---|---|
| Adquisición y registro | Al menos una mascota con 3 o más datos clínicos | Sesión de prueba acompañada, contando lo registrado |
| Retención | Vuelven a abrir o actualizar el perfil en las 2 semanas siguientes, sin que se les pida | Conversación de seguimiento a los 14 días: "¿me muestras la aplicación?", revisando las fechas de los registros |
| Uso real | Usan el perfil o el PDF en una situación real: una cita, un cambio de proveedor, un viaje, una guardería | En el seguimiento: "¿cuándo la usaste? ¿con quién? ¿qué pasó?" |

**Limitaciones de la versión local.** Mientras los datos se guarden solo en el celular de cada participante, el equipo no puede medir nada a distancia: todo se mide observando y conversando. La medición automática llega con la migración a Supabase (ver [sdd.md](sdd.md#qué-sigue)).

Además, Safari en iPhone puede borrar lo que un sitio guardó en el navegador si pasan 7 días sin abrirlo. Para una prueba de dos semanas, pídanles a quienes usen iPhone que agreguen la aplicación a la pantalla de inicio, y tengan lista la feature 004 de respaldo.
