# Sistema de diseño — v0.1

> **Estado:** propuesta inicial, anterior a las entrevistas. Se ajusta con lo que salga de [discovery.md](discovery.md).
> Toda pantalla y todo PDF del producto siguen este documento (principio 8 de la constitution).

---

## 1. Para quién diseñamos

**Valentina, 34 años, Chapinero** — la buyer persona del [brief](brief-corte1.md) (§3). Trabaja tiempo completo, tiene un perro y un gato, y en el último año pasó por una clínica de barrio, una de urgencias y una guardería.

Tres momentos definen el diseño:

| Momento | Dónde está | Qué necesita de la interfaz |
|---|---|---|
| **Registrar** | Saliendo de la consulta, con la mascota en una mano | Terminar en menos de un minuto: la foto primero, pocos campos, nada obligatorio salvo lo esencial |
| **Responder** | En el mostrador de una clínica nueva o en urgencias, con estrés | Encontrar alergias, medicamentos y vacunas sin buscar, y que **quien está al otro lado del mostrador pueda leer la pantalla** |
| **Enviar** | Al dejar a la mascota en la guardería o con un familiar | Un PDF claro, que se lea bien en otro celular o impreso en blanco y negro |

El segundo momento cambia las reglas de un diseño móvil corriente: esa pantalla la leen **dos personas**, y una de ellas está a medio metro de distancia.

Sus hábitos también dictan detalles concretos:

- Las fotos de los carnets ya están en el rollo de su celular → hay que poder **elegirlas de la galería**, no solo tomarlas en el momento.
- Los exámenes le llegan como PDF por WhatsApp → hay que poder **adjuntar un PDF** desde el celular.
- Teme perder años de información → el guardado se **confirma siempre**, y el respaldo está a la vista.

## 2. Principios

1. **La respuesta antes que la navegación.** Al abrir una mascota se ve lo que preguntan, no un menú.
2. **Registrar es más fácil que no registrar.** Si un dato se puede completar después, no se pide ahora.
3. **Legible para dos.** Los datos clave se leen a un brazo de distancia: tamaño, peso y contraste por encima del mínimo.
4. **Calma, no alarma.** Es la salud de alguien querido: tono sereno, y el rojo reservado para alergias y para acciones que borran.
5. **Confianza visible.** Cada guardado se confirma, cada dato dice de cuándo es y cada soporte se puede ver.
6. **Un pulgar.** Las acciones principales viven en la mitad inferior de la pantalla.

## 3. Color

Paleta clara, cálida y sobria. **Todas las combinaciones de esta sección están verificadas contra WCAG AA**: 4,5:1 como mínimo para texto y 3:1 para bordes de controles.

### Base

| Token | Hex | Uso | Contraste verificado |
|---|---|---|---|
| `--color-fondo` | `#F7F6F2` | Fondo de la aplicación | — |
| `--color-superficie` | `#FFFFFF` | Tarjetas, hojas, campos | — |
| `--color-texto` | `#1F2A2E` | Texto principal | 14,7:1 sobre superficie · 13,6:1 sobre fondo |
| `--color-texto-secundario` | `#52606D` | Etiquetas, fechas, metadatos | 6,5:1 sobre superficie · 6,0:1 sobre fondo |
| `--color-borde` | `#E4E1D9` | Divisores decorativos | No aplica: no delimita controles |
| `--color-borde-campo` | `#8A929A` | Borde de campos de formulario | 3,2:1 sobre superficie |

### Marca

| Token | Hex | Uso | Contraste verificado |
|---|---|---|---|
| `--color-primario` | `#0F766E` | Botón principal, enlaces, foco | Texto blanco encima: 5,5:1 · sobre superficie: 5,5:1 · sobre fondo: 5,1:1 |
| `--color-primario-presionado` | `#115E59` | Botón principal presionado | Texto blanco encima: 7,6:1 |
| `--color-primario-suave` | `#E6F4F1` | Selección, chip activo | Primario encima: 4,8:1 · texto encima: 13,0:1 |

### Estados

| Token | Hex | Uso | Contraste verificado |
|---|---|---|---|
| `--color-peligro` / `--color-peligro-suave` | `#B42318` / `#FEF3F2` | Alergias, eliminar | 6,6:1 sobre superficie · 6,1:1 sobre su fondo suave · texto blanco encima: 6,6:1 |
| `--color-advertencia` / `--color-advertencia-suave` | `#B54708` / `#FFFAEB` | Próxima dosis vencida | 5,4:1 · 5,2:1 |
| `--color-exito` / `--color-exito-suave` | `#067647` / `#ECFDF3` | Confirmación de guardado | 5,7:1 · 5,4:1 |

### Familias del historial

Los 8 tipos de evento se agrupan en **3 familias**, para no llenar la pantalla con 8 colores. El color acompaña al ícono y a la etiqueta; nunca es la única pista.

| Familia | Tipos | Color | Fondo suave | Contraste sobre su fondo |
|---|---|---|---|---|
| Prevención | Vacuna, desparasitación | `#0F766E` | `#E6F4F1` | 4,8:1 |
| Atención clínica | Consulta, examen, tratamiento | `#1D4ED8` | `#EFF4FF` | 6,1:1 |
| Seguimiento | Peso, alimentación, comportamiento | `#8A4B1C` | `#FBF3EA` | 6,2:1 |

### Reglas de color

- **El rojo no decora.** Si aparece, algo requiere atención.
- **Nada se comunica solo con color.** Una alergia severa lleva la palabra "Severa"; una vacuna vencida lleva "Vencida".

## 4. Tipografía

Fuente del sistema: carga al instante, no descarga nada y se ve nativa en cada celular.

```css
font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
```

| Token | Tamaño | Peso | Interlineado | Uso |
|---|---|---|---|---|
| `--texto-xs` | 12 px | 400 | 1.4 | Solo metadatos prescindibles ("actualizado hace 2 días") |
| `--texto-sm` | 14 px | 400 | 1.45 | Etiquetas de datos, fechas en listas |
| `--texto-base` | 16 px | 400 | 1.5 | Cuerpo de texto, campos de formulario |
| `--texto-lg` | 18 px | 600 | 1.4 | **Datos de la vista rápida**: alergias, medicamentos, peso |
| `--texto-xl` | 22 px | 600 | 1.3 | Títulos de pantalla |
| `--texto-2xl` | 28 px | 700 | 1.2 | Nombre de la mascota |

Reglas:

- **Nunca menos de 16 px en campos de formulario.** Por debajo, el iPhone hace zoom al tocar el campo y descuadra la pantalla.
- **Números alineados** con `font-variant-numeric: tabular-nums` en pesos, fechas y dosis.
- **Formato colombiano:** decimales con coma (`4,2 kg`) y fechas cortas en español (`14 sept 2026`), con `Intl.NumberFormat('es-CO')` e `Intl.DateTimeFormat('es-CO')`.
- **Microchip en grupos de tres** (`982 000 123 456 789`), para leerlo y dictarlo sin perderse. Se guarda sin espacios.
- La interfaz debe seguir funcionando con la letra del celular al 200 %.

## 5. Espaciado y forma

Escala de 4 px. Nada fuera de la escala.

| Token | Valor | Uso típico |
|---|---|---|
| `--espacio-1` | 4 px | Entre ícono y etiqueta |
| `--espacio-2` | 8 px | Dentro de un grupo |
| `--espacio-3` | 12 px | Relleno de chips y campos |
| `--espacio-4` | 16 px | Margen lateral de la pantalla, relleno de tarjetas |
| `--espacio-5` | 24 px | Entre secciones |
| `--espacio-6` | 32 px | Separaciones mayores |
| `--espacio-7` | 48 px | Antes de las acciones finales |

- **Área táctil mínima de 44 × 44 px**, aunque el ícono se vea más pequeño.
- **Radios:** 8 px en campos y botones, 12 px en tarjetas, 999 px en chips.
- **Sombras:** una sola, suave, para la barra inferior fija. Las tarjetas se separan con borde, no con sombra.
- **Layout:** una columna, con ancho máximo de 480 px centrado en pantallas grandes. Se diseña y se prueba desde 360 px de ancho.

## 6. Componentes base

Inventario inicial. Cada componente contempla los estados que le apliquen: normal, presionado, foco, deshabilitado, cargando y error.

| Componente | Reglas clave |
|---|---|
| **Botón primario** | Fondo primario, texto blanco, 48 px de alto. Uno solo por pantalla |
| **Botón secundario** | Borde y texto primarios sobre superficie |
| **Botón destructivo** | Solo para eliminar, siempre con confirmación |
| **Campo de formulario** | Etiqueta **siempre visible encima** (nunca solo un placeholder). El error aparece debajo, en texto, sin borrar lo escrito |
| **Tarjeta de dato rápido** | Etiqueta en `--texto-sm` secundario y valor en `--texto-lg`. Sin datos, la tarjeta no aparece — salvo vacunas: "Sin vacunas registradas" también es información |
| **Ítem del historial** | Ícono y color de la familia, tipo, dato principal, fecha e indicador de soporte adjunto |
| **Selector de tipo** | Cuadrícula de 8 botones grandes, con ícono y nombre. Un solo toque |
| **Chip de filtro** | Filtra el historial por tipo |
| **Adjuntar soporte** | Dos opciones visibles: **Tomar foto** y **Elegir archivo** (galería o PDF). Muestra la miniatura al elegir |
| **Confirmación** | Aviso breve en la parte inferior ("Vacuna guardada"), con `role="status"`, visible 4 segundos |
| **Estado vacío** | Una frase y la acción que lo resuelve. Sin ilustraciones pesadas |
| **Barra de acciones inferior** | Fija. Las dos acciones del perfil: **Registrar** y **Compartir PDF** |

## 7. Íconos

- Una sola familia: **Lucide** (lucide.dev, licencia libre). Se copia el SVG de cada ícono al proyecto, sin instalar dependencias.
- Trazo de 2 px; 24 px de tamaño (20 px dentro de listas).
- En las acciones principales, el ícono va **siempre acompañado de texto**.

Íconos sugeridos (verifiquen el nombre exacto en lucide.dev):

| Uso | Ícono |
|---|---|
| Vacuna | `syringe` |
| Desparasitación | `shield-check` |
| Consulta | `stethoscope` |
| Examen | `flask-conical` |
| Tratamiento | `pill` |
| Peso | `weight` |
| Alimentación | `utensils` |
| Comportamiento | `paw-print` |
| Alergia | `triangle-alert` |
| Compartir PDF | `file-text` |

## 8. Voz y tono

- **Tuteo**, como el brief ("tu mascota").
- **Las palabras del dueño, no las del sistema:**

| En la interfaz decimos | No decimos |
|---|---|
| Registrar | Crear evento |
| Historial | Línea de tiempo, timeline |
| Foto o PDF | Adjunto, archivo, soporte |
| Medicamentos actuales | Medicación vigente |
| Microchip o placa | Identificador |
| Guardado | Operación exitosa |

- **Confirmaciones concretas:** "Vacuna guardada", no "Listo".
- **Errores que dicen qué pasó y qué hacer, sin culpar:** "No pudimos guardar la foto. Tu registro sí quedó guardado: intenta adjuntarla otra vez".
- **Borrar siempre pregunta y dice la consecuencia:** "¿Eliminar este registro? No se puede deshacer".
- **Estados vacíos que invitan:** "Aún no hay registros. Empieza por la última vacuna".

## 9. El reporte PDF

El PDF es la cara del producto ante un veterinario que nunca ha oído hablar de la aplicación. Tiene sus propias reglas:

- **Tamaño carta**, márgenes de 18 mm. Se lee bien **impreso en blanco y negro**: nada depende del color.
- **Encabezado:** nombre de la mascota, especie, raza, edad, microchip o placa, y una foto pequeña.
- **Justo debajo, siempre:** "Generado el 15 sept 2026 · Información registrada por el propietario". Le dice al profesional de cuándo es el dato y quién lo escribió.
- **Primero el resumen**, igual a la vista rápida: alergias dentro de un recuadro de borde grueso con la palabra **ALERGIAS**, medicamentos actuales, últimas vacunas y peso.
- **Después, una sección por cada tipo elegido**, en tabla: fecha · detalle · lugar · soporte.
- **Cuerpo de 10 a 11 pt**, títulos de 14 pt, números alineados.
- **Pie de página:** "Página 1 de 3".

## 10. Movimiento

- Transiciones de 150 a 200 ms, solo para dar continuidad: abrir una hoja, confirmar un guardado.
- Con `prefers-reduced-motion` activo, sin animaciones.

## 11. Accesibilidad: mínimos no negociables

- Contraste AA en todo (sección 3, ya verificado).
- Foco visible en todo elemento interactivo: contorno de 2 px en `--color-primario`, separado 2 px del elemento.
- Cada `<label>` asociado a su campo.
- Toda imagen de soporte con texto alternativo ("Foto del carnet de vacunas, 14 sept 2026").
- Nada que solo se entienda por el color.

## 12. Variables CSS

Listas para pegar en la hoja de estilos base. Es la única fuente de estos valores en el código.

```css
:root {
  /* Base */
  --color-fondo: #F7F6F2;
  --color-superficie: #FFFFFF;
  --color-texto: #1F2A2E;
  --color-texto-secundario: #52606D;
  --color-borde: #E4E1D9;
  --color-borde-campo: #8A929A;

  /* Marca */
  --color-primario: #0F766E;
  --color-primario-presionado: #115E59;
  --color-primario-suave: #E6F4F1;

  /* Estados */
  --color-peligro: #B42318;
  --color-peligro-suave: #FEF3F2;
  --color-advertencia: #B54708;
  --color-advertencia-suave: #FFFAEB;
  --color-exito: #067647;
  --color-exito-suave: #ECFDF3;

  /* Familias del historial */
  --color-prevencion: #0F766E;
  --color-prevencion-suave: #E6F4F1;
  --color-clinica: #1D4ED8;
  --color-clinica-suave: #EFF4FF;
  --color-seguimiento: #8A4B1C;
  --color-seguimiento-suave: #FBF3EA;

  /* Tipografía */
  --fuente: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  --texto-xs: 0.75rem;
  --texto-sm: 0.875rem;
  --texto-base: 1rem;
  --texto-lg: 1.125rem;
  --texto-xl: 1.375rem;
  --texto-2xl: 1.75rem;

  /* Espaciado */
  --espacio-1: 0.25rem;
  --espacio-2: 0.5rem;
  --espacio-3: 0.75rem;
  --espacio-4: 1rem;
  --espacio-5: 1.5rem;
  --espacio-6: 2rem;
  --espacio-7: 3rem;

  /* Forma */
  --radio-control: 8px;
  --radio-tarjeta: 12px;
  --radio-chip: 999px;
  --area-tactil: 44px;
  --ancho-maximo: 480px;
}
```

## 13. Pendiente de validar en discovery

- ¿La vista rápida se lee desde el otro lado del mostrador? Probarlo con un celular real, a 50 cm.
- ¿Las 3 familias de color ayudan a ubicarse en el historial o confunden?
- ¿Los dueños dicen "registro", "historial", "carnet"? Ajustar el vocabulario a sus palabras reales.
- ¿El PDF que esperan los veterinarios se parece al de la sección 9?

**Fuera de la v0.1:** modo oscuro. Como todo color sale de las variables de la sección 12, agregarlo después no obliga a tocar los componentes.
