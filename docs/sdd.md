# SDD — Hoja de ruta del proyecto

**Plataforma de mascotas · Lenguajes Digitales 5 · Universidad El Bosque**
Samuel Parada · Andrés Claros
Basada en [brief-corte1.md](brief-corte1.md) (versión 3) y en la guía de sesión de Spec-Driven Development del curso.

---

Este documento sigue las fases de la guía, en el mismo orden, con cada *"información por completar sobre tu proyecto"* ya resuelta. Los bloques de texto están listos para pegar en el chat de Claude Code.

> **Regla de la guía:** lo que trae el equipo vive en `docs/`; lo que genera Spec Kit vive en `.specify/`, `.claude/` y `specs/`, y no se mezclan. Por eso aquí no hay specs, planes ni tareas: está lo que ustedes le entregan a Spec Kit para que los genere.

## Estado

| Fase | Qué | Estado |
|---|---|---|
| 0 | Repositorio en GitHub | ✅ `samuel81194/plataforma-mascotas` (privado). Falta invitar a Andrés |
| 1 | Documentos base en `docs/` | ✅ Listos para revisar |
| 2 | Instalar Spec Kit | ✅ Integración Claude, scripts PowerShell y extensión git |
| 3 | Constitution | 📝 Texto listo |
| 4 | Specify | 📝 Textos listos para las 4 features |
| 5 | Plan | 📝 Texto listo |
| 6 | Tasks | ⬜ Se corre después del plan |

---

## Fase 0 — Repositorio ✅

> **Hecho el 15 de septiembre de 2026:** repositorio privado [`samuel81194/plataforma-mascotas`](https://github.com/samuel81194/plataforma-mascotas), clonado en `C:\Users\samue\dev\plataforma-mascotas`, con la identidad de git configurada solo para ese repositorio.
>
> **Pendiente:** invitar a Andrés en GitHub (*Settings → Collaborators → Add people*). Él solo tiene que aceptar la invitación, clonar el repositorio fuera de OneDrive y abrirlo con Claude Code: no necesita instalar `uv` ni Spec Kit, porque `.specify/` y `.claude/` ya están en el repositorio.

Los pasos, como referencia para cualquier computador nuevo:

1. **Creen un repositorio privado en GitHub** y agréguense los dos como colaboradores. Nombre sugerido: `plataforma-mascotas`.
2. **Clónenlo en VS Code:** `Ctrl+Shift+P → Git: Clone → pegar la URL del repo → elegir carpeta`.
   **Elijan una carpeta fuera de OneDrive** (por ejemplo `C:\dev\`): la sincronización de OneDrive puede dañar la carpeta `.git` o crear conflictos cuando se trabaja desde dos computadores.
3. **Copien a esa carpeta** `docs/`, `.gitignore` y `README.md`.
4. **Primer commit y push**, en la terminal de VS Code, un comando por línea:
   ```powershell
   git add .
   git commit -m "docs: documentos base del proyecto"
   git push
   ```
5. **Abran la extensión de Claude Code** e inicien sesión.

Si es el primer commit desde ese computador, git pedirá configurar la identidad:

```powershell
git config --global user.name "Tu Nombre"
git config --global user.email "tu-correo@unbosque.edu.co"
```

---

## Fase 1 — Documentos base ✅

| Archivo | Qué contiene | Qué les toca hacer |
|---|---|---|
| `.gitignore` | El de la guía, más `desktop.ini` (Windows lo crea en carpetas de OneDrive) | Nada |
| [`brief-corte1.md`](brief-corte1.md) | El brief v3, tal cual | Mantenerlo al día: es un documento vivo |
| [`discovery.md`](discovery.md) | 10 supuestos priorizados, guion para dueños y para receptores, criterios de decisión | Revisar los criterios **antes** de la primera entrevista, y salir a entrevistar |
| [`design-system.md`](design-system.md) | Principios, paleta con contraste verificado, tipografía, espaciado, componentes, tono y diseño del PDF, pensados para Valentina | Revisarlo y ajustarlo después de discovery |
| [`design-references/README.md`](design-references/README.md) | Qué referencias buscar y cómo nombrarlas | Llenar la carpeta |
| [`flujo-pantallas.md`](flujo-pantallas.md) | Placeholder con estructura | Completarlo después de las entrevistas |
| `sdd.md` | Este documento | Ir marcando el avance en la tabla de estado |

`sdd.md` es el único archivo que la guía no pide. Guarda los textos de cada comando para que no dependan del historial de un chat.

---

## Fase 2 — Instalar Spec Kit ✅

> **Hecho el 15 de septiembre de 2026**, con tres diferencias frente a la guía, todas por cambios de la versión actual de Spec Kit (1.0.8.dev0):
>
> 1. **El `init` llevó tres opciones más:** `specify init --here --integration claude --script ps --force --non-interactive --ignore-agent-tools`.
>    - `--ignore-agent-tools`: `specify check` busca el programa `claude` en la terminal; con la app de escritorio o la extensión de VS Code no lo encuentra, aunque Claude Code sí está disponible.
>    - `--force` y `--non-interactive`: evitan preguntas que se quedan esperando respuesta cuando el comando no corre en una terminal interactiva.
> 2. **Se instaló la extensión git** (`specify extension add git`). En esta versión, crear la rama `001-nombre` al correr `/speckit-specify` ya no viene en el núcleo de Spec Kit: sin la extensión se crea la carpeta `specs/001-.../`, pero no la rama que describe la guía. La extensión viene incluida en Spec Kit, tiene los commits automáticos desactivados (`.specify/extensions/git/git-config.yml`) y nunca hace push.
> 3. **No hace falta PowerShell 7.** Los scripts de `.specify/scripts/powershell/` se probaron con el PowerShell 5.1 que trae Windows.

Los pasos de la guía, como referencia. En la terminal de VS Code (PowerShell):

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Cierren y vuelvan a abrir la terminal para que reconozca `uv`, y sigan:

```powershell
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
specify check
specify init --here --integration claude --script ps
```

- `--here`, porque el repositorio ya tiene contenido.
- `--script ps`, porque PowerShell es la opción que funciona igual en las salas (Windows) y en Mac.
- Aparecen `.specify/` y `.claude/`. Se suben a git como cualquier archivo: **hagan commit y push antes de seguir**. Así, cualquier computador que clone el repo ya tiene los comandos `/speckit-*`, sin reinstalar nada.

---

## Fase 3 — Constitution

Los principios que gobiernan todo lo que se construya después. Salen del brief y del sistema de diseño.

**Antes de empezar:** abran Claude Code **en la carpeta del repositorio** (`C:\Users\samue\dev\plataforma-mascotas`). En VS Code: *File → Open Folder*; en la app de escritorio: una sesión nueva con esa carpeta. Los comandos `/speckit-*` solo aparecen en sesiones abiertas ahí.

En el chat de Claude Code:

```text
/speckit-constitution

Este proyecto sigue estos principios:

1. El dueño es la única persona que crea, edita y elimina la información
   de su mascota. Veterinarios, cuidadores y guarderías no tienen
   cuenta: reciben solo lo que el dueño decide mostrar o enviar.
2. Web responsive, mobile-first desde 360 px de ancho y usable con una
   sola mano; sin app nativa ni hardware adicional.
3. Registrar un evento toma menos de un minuto: fecha de hoy por
   defecto, un solo campo obligatorio por tipo y la foto o el PDF del
   soporte. Si una funcionalidad hace más lento el registro, se rediseña.
4. Lo que más se pregunta va primero: identificación, alergias,
   medicación vigente, últimas vacunas y peso, sin tener que buscar.
5. Compartir no le exige nada a quien recibe: un PDF que el dueño envía
   por el medio que prefiera, sin cuenta ni aplicación del otro lado.
6. Reserva por defecto (Ley 576 de 2000 y Ley 1581 de 2012): nadie
   distinto al dueño accede a la información sin una acción explícita
   suya, y lo que se comparte contiene solo lo que él eligió.
7. La información nunca se pierde en silencio: cada guardado se confirma
   visualmente y el dueño puede sacar un respaldo de todo.
8. Toda interfaz y todo PDF siguen estrictamente docs/design-system.md.
9. Datos reales desde el inicio: ninguna pantalla se da por terminada
   mientras muestre datos inventados en el código.
10. Código simple, que el equipo pueda leer y modificar. No se agrega una
    librería o herramienta sin una razón escrita en el plan.
11. Una feature está terminada solo cuando su quickstart.md pasa en un
    celular real.
12. Fuera de alcance del semestre: avatar 3D, recordatorios genéricos,
    IA, alertas de vacunas y controles, emisión de identificadores,
    lectura automática de microchip o QR, permisos granulares o
    vencimientos al compartir, e integración con veterinarias o
    aseguradoras.
```

Resultado: `.specify/memory/constitution.md`.

**De dónde sale cada principio**

| # | Fuente |
|---|---|
| 1 | Brief §2 y §6: el veterinario no necesita cuenta ni acceso de edición |
| 2 | Brief §2 (consulta desde el celular) y §6 (sin lectura automática de microchip) |
| 3 | Brief §2 y la persona de §3: si registrar es más complicado que tomar una foto, Valentina no lo sostiene |
| 4 | Brief §2 y §6: vista de acceso rápido |
| 5 | Brief §6: compartir mediante reporte en PDF |
| 6 | Brief §1 y fuente 6 (Ley 576 de 2000, art. 61); Ley 1581 de 2012 por los datos personales del dueño |
| 7 | Objeción de Valentina (brief §3) y principio 5 de design-system.md |
| 8 | Guía del curso |
| 9 | Restricción del curso: el MVP se demuestra con datos reales guardados, no con maquetas |
| 10 | Guía del curso: el equipo tiene bases de frontend básico |
| 11 | Guía del curso: `quickstart.md` como prueba manual de cada feature |
| 12 | Brief §6 (visión futura y fuera de alcance). Las alertas aparecen en la oferta de §3, pero no entre los cuatro mecanismos del semestre |

---

## Fase 4 — Specify

Una feature a la vez. Cada corrida crea una rama `00N-nombre` (la crea la extensión git instalada en la Fase 2) y una carpeta `specs/00N-nombre/` con su `spec.md`. Al terminar cada feature, integren su rama a `main` antes de empezar la siguiente.

### Mapa de features

Los cuatro mecanismos del brief (§6) quedan en tres features, más una cuarta que aparece por guardar los datos en el navegador:

| # | Feature | Qué cubre del brief | Depende de |
|---|---|---|---|
| **001** | Perfil e historial de la mascota | Perfil con línea de tiempo + identificador como dato del perfil | — |
| **002** | Vista de acceso rápido | Vista de acceso rápido | 001 |
| **003** | Reporte PDF para compartir | Compartir mediante un reporte en PDF | 001, y reusa el resumen de 002 |
| **004** | Respaldo de la información | Objeción de Valentina (§3) | 001 |

**Sobre la 004:** no está entre los cuatro mecanismos, pero se vuelve necesaria mientras los datos vivan solo en el navegador. Si el dueño borra los datos de navegación o cambia de celular, lo pierde todo, que es justo el miedo de Valentina. Es obligatoria antes de dejar la aplicación en manos de dueños reales durante dos semanas; si para entonces ya migraron a Supabase, se replantea.

**Orden de trabajo:** un ciclo completo por feature antes de empezar la siguiente:
`specify → clarify (opcional) → plan → tasks → implement → probar el quickstart`

### 001 — Perfil e historial de la mascota · *la primera*

Va primero porque es el hábito del que depende todo lo demás (supuesto S1 de discovery): sin registros no hay vista rápida que mostrar ni PDF que enviar.

```text
/speckit-specify

Construir el perfil de la mascota con su historial, basado en
@docs/brief-corte1.md.

El dueño crea el perfil de su perro o gato: nombre y especie son
obligatorios; raza, sexo, fecha de nacimiento, esterilizado, foto y el
número de microchip o el código de placa (escrito a mano) son
opcionales. Puede tener varias mascotas. También registra las alergias
conocidas.

Registra cada evento apenas ocurre, en menos de un minuto desde el
celular: elige el tipo, la fecha viene con el día de hoy, llena pocos
campos y adjunta la foto o el PDF del soporte, ya sea tomando la foto en
el momento, eligiéndola de la galería o subiendo un PDF que le llegó por
WhatsApp. Es el dueño quien registra el resultado de cada consulta; el
veterinario no tiene cuenta.

Tipos de evento y sus campos. Además de la fecha, el primer campo de
cada tipo es el único obligatorio:
- Vacuna: nombre de la vacuna, laboratorio o lote, próxima dosis, quién la aplicó
- Desparasitación: producto, vía (interna o externa), próxima dosis
- Consulta: motivo, diagnóstico, veterinario, clínica
- Examen: tipo de examen, laboratorio, resumen del resultado
- Tratamiento: medicamento, dosis, frecuencia, fecha de fin (vacía si
  sigue vigente); la fecha del evento es la de inicio
- Peso: valor en kg
- Alimentación: producto, tipo (seco, húmedo, casero o mixto), cantidad diaria
- Comportamiento: descripción

El historial muestra los eventos del más reciente al más antiguo, se
puede filtrar por tipo, y cada evento se puede abrir, editar o eliminar.
Cada acción confirma visualmente que quedó guardada, siguiendo
@docs/design-system.md.

Prioridad: primero crear una mascota y registrar un evento con su foto;
después editar, eliminar, filtrar y alergias.

Fuera de alcance: vista de acceso rápido, reporte PDF, respaldo,
recordatorios o alertas, lectura automática de microchip o QR, cuentas
para veterinarios.
```

**Preguntas que probablemente salgan en `/speckit-clarify`**, con una respuesta sugerida:

- *¿Cuántos soportes por evento, y de qué tamaño?* → Hasta 5 por evento; las fotos se comprimen y los PDF pesan como máximo 10 MB.
- *¿Qué pasa con los eventos al eliminar una mascota?* → Se eliminan con ella, después de confirmar.
- *¿Se aceptan fechas pasadas y futuras?* → Pasadas sí: es lo normal al cargar el historial viejo. Futuras no, salvo la próxima dosis.

### 002 — Vista de acceso rápido

```text
/speckit-specify

Construir la vista de acceso rápido del perfil, basada en
@docs/brief-corte1.md y en el perfil e historial de la feature 001.

Al abrir el perfil de una mascota, lo primero que se ve —sin buscar ni
desplazarse, en un celular— es lo que más se pregunta: identificación
(incluido el microchip o la placa), alergias, medicación vigente
(tratamientos sin fecha de fin o con fecha de fin futura), últimas
vacunas con su próxima dosis, y el peso actual con su variación frente
al registro anterior. Todo sale de lo ya registrado: el dueño no llena
nada aparte. La pantalla también debe poder leerla la persona que la
mira desde el otro lado del mostrador. El historial completo queda un
nivel más abajo. Sigue @docs/design-system.md.

Fuera de alcance: reporte PDF, notificaciones o recordatorios.
```

Probables aclaraciones: *¿cuántas vacunas mostrar?* → las 3 más recientes. *¿Qué pasa con un bloque sin datos?* → no se muestra, salvo vacunas ("Sin vacunas registradas"), como define design-system.md.

### 003 — Reporte PDF para compartir

```text
/speckit-specify

Construir el reporte en PDF para compartir, basado en
@docs/brief-corte1.md.

Desde el perfil de su mascota, el dueño genera en segundos un PDF con
toda la información o solo con las secciones que elija para ese momento
(identificación, alergias, medicación vigente, vacunas,
desparasitaciones, consultas, exámenes, tratamientos, peso, alimentación
y comportamiento), y lo comparte por el medio que prefiera: WhatsApp,
correo o impreso. Quien lo recibe no necesita cuenta ni la aplicación.

El PDF empieza con el resumen de acceso rápido, dice la fecha en que se
generó y que la información fue registrada por el propietario, incluye
las fotos de los soportes de las secciones elegidas y se lee bien
impreso en blanco y negro. Sigue @docs/design-system.md.

Fuera de alcance: enlaces con permisos o vencimiento, envío directo a
sistemas de veterinarias, firma digital.
```

Probables aclaraciones: *¿los soportes que ya son PDF (exámenes) van dentro del reporte o solo se mencionan?* · *¿se incluyen los datos de contacto del dueño?* → sugerencia: solo si él lo elige al generar el reporte · *¿se filtra por fechas?* → sugerencia: no en esta versión.

**Notas para el `/speckit-plan` de esta feature:** el PDF se genera dentro del navegador, sin enviar la información a ningún servicio externo (principio 6). En `research.md` conviene comparar una librería de PDF (por ejemplo jsPDF) con una hoja de estilos de impresión. Para enviarlo desde el celular, la Web Share API abre WhatsApp con el archivo adjunto donde el navegador lo permite; si no, el PDF se descarga. Confirmen con el profesor si una librería de PDF cabe dentro de "sin frameworks".

### 004 — Respaldo de la información

```text
/speckit-specify

Construir el respaldo de la información, basado en @docs/brief-corte1.md
y en la objeción de Valentina: "¿y si dejo de usarla, pierdo la
información de años de mis mascotas?".

El dueño descarga en un solo archivo toda la información de sus
mascotas, incluidos los soportes, y la puede restaurar en otro navegador
o en otro celular. La aplicación muestra la fecha del último respaldo.
Sigue @docs/design-system.md.

Fuera de alcance: sincronización en la nube, cuentas de usuario.
```

**Notas para el `/speckit-plan` de esta feature:** pedir almacenamiento persistente al navegador (`navigator.storage.persist()`) y verificar en un iPhone que Safari no borre los datos después de 7 días sin abrir la aplicación. Si los borra, agregar la aplicación a la pantalla de inicio lo evita.

> **Recordatorio de la guía:** si un `spec.md` cambia después de haber corrido `/speckit-plan` o `/speckit-tasks`, esos archivos quedan desactualizados y hay que volver a correrlos.

---

## Fase 5 — Plan

Se corre después de cada `/speckit-specify` (y de `/speckit-clarify`, si lo usan). Es el texto de la guía, tal cual, más un párrafo propio de este proyecto:

```text
/speckit-plan

Construir esto como una aplicación web simple: HTML, CSS y JavaScript
sin frameworks — el equipo tiene bases de frontend básico, no React.
Por ahora sin backend real: los datos se guardan localmente en el
navegador (localStorage). Prioriza pantallas fáciles de leer y
modificar, y una estructura de archivos simple de navegar.

Para este proyecto: los registros van en localStorage, pero las fotos y
los PDF de soporte van en IndexedDB, porque localStorage solo admite
unos 5 MB por sitio y se llenaría con pocas fotos. Las fotos se
comprimen en el navegador antes de guardarse. Colores, tipografía y
espaciados salen de las variables CSS de @docs/design-system.md.
```

**Por qué el párrafo extra.** Los soportes (fotos de carnets, PDF de exámenes) son centrales en la feature 001, y localStorage solo guarda texto, con un límite de pocos megas por sitio. Guardar fotos ahí funcionaría en la primera prueba y fallaría con el uso real. IndexedDB también guarda los datos dentro del navegador —sigue sin haber backend, como pide la guía—, pero admite archivos y mucho más espacio. Si el curso exige usar el texto de la guía sin cambios, háblenlo con el profesor antes de correr el plan.

Resultado: `plan.md` y probablemente `data-model.md`, `research.md` y `quickstart.md`, dentro de `specs/00N-.../`.

---

## Fase 6 — Tasks

```text
/speckit-tasks
```

Resultado: `tasks.md` en la misma carpeta de la feature, el checklist real de construcción. Commit y push para cerrar la sesión.

---

## Qué sigue

1. **`/speckit-implement`**: Claude construye el código tarea por tarea, siguiendo `tasks.md`. Va en la próxima sesión.
2. **Probar con `quickstart.md` en un celular real.** Algunas funciones del navegador que usa este proyecto, como compartir el PDF por WhatsApp, solo funcionan con HTTPS. Publiquen la aplicación en GitHub Pages (en repositorios privados requiere GitHub Pro, que es gratis con el GitHub Student Developer Pack) o en Netlify.
3. **Siguiente feature:** volver a la Fase 4 con la 002, luego la 003 y luego la 004.
4. **En paralelo, la investigación:** entrevistas de [discovery.md](discovery.md) → [flujo-pantallas.md](flujo-pantallas.md) → [design-system.md](design-system.md) aplicado.
5. **Migración a Supabase.** Con la investigación, el flujo de pantallas y el sistema de diseño aplicados, se vuelve a `/speckit-plan` para reemplazar el almacenamiento local por Supabase, y de ahí a `/speckit-tasks` y `/speckit-implement`. Conviene llegar con estas decisiones pensadas, para incluirlas en ese prompt:
   - **Cuentas de dueño** con Supabase Auth: es el momento en que aparece el inicio de sesión.
   - **Eventos en una sola tabla**, con el tipo en una columna y los campos propios en un campo JSON validado por la aplicación. El historial sale de una sola consulta ordenada por fecha, y agregar un tipo nuevo no obliga a migrar la base.
   - **Seguridad a nivel de fila (RLS) en todas las tablas**: cada dueño lee y escribe solo lo suyo. Es el principio 6 aplicado a la base de datos.
   - **Soportes en un bucket privado**, entregados con URL firmadas de vida corta.
   - **Traer lo que ya está en los navegadores:** el archivo de respaldo de la feature 004 sirve para subir los datos locales a la cuenta nueva.
   - **Medir la hipótesis a distancia:** con los datos en un servidor ya se pueden contar las tres señales de [discovery.md](discovery.md) (sección 9).

### Secuencia sugerida

| Paso | Construcción (Spec Kit) | Investigación y diseño (`docs/`) |
|---|---|---|
| 1 | Fases 0, 2 y 3 | Revisar design-system.md y los criterios de discovery.md; empezar a reclutar |
| 2 | Ciclo de la 001 | Entrevistas a dueños y receptores |
| 3 | Ciclo de la 002 | Síntesis de discovery → flujo-pantallas.md |
| 4 | Ciclo de la 003 | Ajustar design-system.md y el brief con los hallazgos |
| 5 | Ciclo de la 004 | Preparar la prueba de la hipótesis |
| 6 | Migración a Supabase | Prueba con dueños reales durante 2 semanas |

**Reparto sugerido:** Andrés lleva la columna de construcción (conduce los comandos y revisa lo que genera cada uno) y Samuel la de investigación y diseño. Cada uno revisa el trabajo del otro antes de hacer commit.

---

## Trazabilidad con el brief v3

| Brief | Dónde queda |
|---|---|
| §1 Problema y pregunta central | discovery.md: S2, S3 y S4 |
| §2 Objetivo: registrar apenas ocurre, vista rápida, mostrar sin cuenta | Constitution: principios 3, 4 y 5 · features 001, 002 y 003 |
| §3 Segmento | discovery.md: filtro de entrevistados |
| §3 Valentina | design-system.md §1 · detalles de la 001 (galería, PDF de WhatsApp) · feature 004 · discovery.md S9 |
| §3 Modelo de ingresos: suscripción única | discovery.md S10 (exploratorio). El producto no tiene pantalla de pago ni límite de mascotas |
| §4 Hipótesis y sus tres señales | discovery.md §9 |
| §4 Datos que faltan | discovery.md: guion para dueños |
| §5 Propuesta secundaria (quien recibe) | discovery.md: guion para receptores, S5 y S6 · diseño del PDF en design-system.md §9 |
| §6 Perfil con línea de tiempo | Feature 001 |
| §6 Vista de acceso rápido | Feature 002 |
| §6 Compartir mediante reporte PDF | Feature 003 |
| §6 Identificador como dato del perfil | Feature 001 |
| §6 Visión futura y fuera de alcance | Constitution: principio 12 |

## Qué cambió frente al SDD anterior

El SDD anterior, escrito sobre el brief v2, se reemplaza por esta estructura.

| Antes (brief v2) | Ahora (brief v3 y guía del curso) |
|---|---|
| Compartir con un enlace público revocable | Reporte PDF, completo o por secciones, enviado por el medio que el dueño elija |
| Freemium: una mascota gratis y pantalla de pago | Una sola versión por suscripción: varias mascotas desde el inicio y sin pantalla de pago en el producto |
| Tercera señal de la hipótesis: llegar a la pantalla de pago | Tercera señal: usar el perfil en una situación real |
| Stack por decidir (se recomendaba Next.js + Supabase) | HTML, CSS y JavaScript sin frameworks, con los datos en el navegador; Supabase más adelante (guía del curso) |
| Diez documentos técnicos escritos a mano: requisitos, modelo de datos, API, arquitectura, pruebas, roadmap y ADR | Documentos base en `docs/`. La spec, el plan, el modelo de datos y las tareas los genera Spec Kit, una feature a la vez |
| Sin buyer persona | Valentina guía el sistema de diseño, las entrevistas y los detalles de cada feature |
