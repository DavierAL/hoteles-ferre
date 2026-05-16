# Design System — Hoteles Ferré

> **Fuente:** Brandbook Hoteles Ferré 2026 v4
> **Propósito:** Traducir la identidad de marca a un sistema de diseño accionable para producto digital, web, app y piezas gráficas.
> **Última actualización:** 2026-05-07

---

## 0. TL;DR — Decisiones de diseño en una página

| Dimensión | Decisión |
|-----------|----------|
| **Arquetipo de marca** | El Cuidador Sofisticado |
| **Promesa** | Elegancia + Calidez |
| **Estilo visual** | Minimalismo cálido / Editorial sobrio |
| **Paleta** | Bicromía Onix + Beige (negro y blanco están prohibidos como base) |
| **Tipografía** | Calm Serif (display) + Montserrat (UI/cuerpo) |
| **Lenguaje gráfico** | Trazo orgánico de grosor variable (extensión del isotipo) |
| **Forma característica** | Curvas envolventes, nunca cajas rígidas |
| **Fotografía** | Documental humano, luz natural, contrastes bajos |
| **Tono UX** | Anfitrión, no anunciante. Claro, humano, seguro |
| **Densidad** | Baja. "Menos es más. El color acompaña, no domina." |
| **Anti-patrón clave** | Frialdad corporativa Y informalidad económica |

---

## 1. Fundamentos de marca

### 1.1 Manifiesto (resumen accionable)

Hoteles Ferré rechaza la despersonalización de la industria hotelera. El producto digital debe reflejar **presencia, criterio y cuidado** — nunca automatismo frío. Cada interfaz "mira al huésped a los ojos": reconoce, acompaña, atiende.

**Implicancias para producto:**
- Onboarding y check-in digital deben sentirse como una conversación, no un formulario.
- Mensajes de error y confirmación se redactan como un anfitrión hablaría, no como un sistema.
- Las pantallas de carga, vacío y éxito son oportunidades para reforzar calidez, no espacios muertos.
- Evitar lenguaje transaccional ("reserva procesada") → usar lenguaje humano ("lo esperamos el viernes 12").

### 1.2 Posicionamiento

> Única cadena hotelera peruana que conecta Costa, Sierra y Selva con sofisticación 4–5★ y trato familiar directo.

**Tensión central a comunicar:** *Elegancia + Calidez.*

| ✅ Sí somos | ❌ No somos |
|------------|------------|
| Sofisticados | Lujo distante / corporativo frío |
| Cercanos y humanos | Económicos / informales |
| Locales y conocedores | Genéricos / globalizados |
| Disciplinados e impecables | Rígidos / acartonados |

### 1.3 Arquetipo: El Cuidador Sofisticado

| Rasgo | Cómo se expresa en UI |
|-------|----------------------|
| **Impecable** | Espaciados consistentes, alineaciones precisas, cero glitches visuales |
| **Cercano** | Microcopy en primera persona plural ("le acompañamos"), sin jerga |
| **Seguro** | Una sola CTA primaria por pantalla, jerarquía clara, sin ambigüedad |
| **Local y conocedor** | Recomendaciones contextuales por destino (Costa/Sierra/Selva), no genéricas |

### 1.4 Tono de comunicación

| ✅ Cómo hablamos | ❌ Cómo NO hablamos |
|------------------|---------------------|
| Claro y preciso | Lenguaje corporativo vacío |
| Humano y directo | Frases genéricas de hotelería |
| Seguro, nunca arrogante | Promesas exageradas |

**Ejemplos UX:**

| Situación | ❌ Evitar | ✅ Preferir |
|-----------|-----------|-------------|
| Confirmación de reserva | "Su transacción ha sido procesada exitosamente" | "Listo. Lo esperamos el viernes 12." |
| Error de pago | "Error 402. Operación rechazada." | "El pago no se completó. Probemos otro método." |
| Estado vacío | "No hay resultados" | "Aún no hay reservas. Cuando reserve, las verá aquí." |
| Botón principal | "Submit" / "Procesar" | "Reservar" / "Confirmar mi estadía" |

---

## 2. Sistema de color

> *"Menos es más. El color acompaña, no domina."*

### 2.1 Paleta principal — Bicromía estricta

La marca opera en bicromía. **No usar negro puro (#000000) ni blanco puro (#FFFFFF) como base.**

| Token | Nombre | Hex (estimado del brandbook) | Uso |
|-------|--------|------------------------------|-----|
| `--color-onix` | Onix | `#141414` | Fondo oscuro, tipografía sobre claro, isotipo |
| `--color-beige` | Beige | `#EFE7D5` | Fondo claro, tipografía sobre oscuro, contenedores cálidos |

> **Nota técnica:** los hex son una aproximación visual del PDF. El equipo de marca debe confirmar los valores exactos (Pantone / CMYK / RGB / HEX) antes de producción.

### 2.2 Tokens semánticos (sistema extendido para producto)

Para construir interfaces digitales reales se necesita una escala. Esta extensión respeta la bicromía manteniendo Onix y Beige como anclas.

```css
:root {
  /* Anclas de marca — NO modificar */
  --color-onix:        #141414;
  --color-beige:       #EFE7D5;

  /* Escala Onix (oscuros) — sólo para jerarquía sobre fondo beige */
  --color-onix-900:    #141414; /* base */
  --color-onix-700:    #2A2A2A;
  --color-onix-500:    #4A4A4A; /* texto secundario */
  --color-onix-300:    #8A8A8A; /* texto auxiliar / disabled */

  /* Escala Beige (claros) — sólo para jerarquía sobre fondo onix */
  --color-beige-100:   #FAF6EC; /* highlight sobre onix */
  --color-beige-200:   #EFE7D5; /* base */
  --color-beige-300:   #DDD3BD; /* divisor sobre beige */
  --color-beige-400:   #C4B89C; /* énfasis decorativo */

  /* Semánticos UI */
  --bg-primary:        var(--color-beige-200);
  --bg-inverse:        var(--color-onix-900);
  --text-primary:      var(--color-onix-900);
  --text-secondary:    var(--color-onix-500);
  --text-on-dark:      var(--color-beige-200);
  --border-subtle:     var(--color-beige-300);

  /* Estados funcionales (mínimos, restringidos) */
  --color-success:     #4F6A4A; /* verde apagado, no neón */
  --color-warning:     #B5894A; /* ámbar tostado */
  --color-error:       #A14A3F; /* terracota, no rojo puro */
  --color-info:        var(--color-onix-700);
}
```

**Reglas:**
1. **Nunca** introducir color saturado fuera de los estados funcionales.
2. Los estados funcionales se acompañan **siempre** de ícono + texto (regla `color-not-only`). El color por sí solo no comunica.
3. Para gráficos/charts, derivar la escala desde Onix → Beige (degradados monocromáticos), no introducir paleta categórica de colores.

### 2.3 Combinaciones permitidas

| Fondo | Texto principal | Texto secundario | Acento |
|-------|-----------------|------------------|--------|
| `--color-beige-200` | `--color-onix-900` | `--color-onix-500` | `--color-onix-700` |
| `--color-onix-900` | `--color-beige-200` | `--color-beige-300` | `--color-beige-100` |

**Contrastes verificados (WCAG AA):**
- Onix `#141414` sobre Beige `#EFE7D5`: ratio ~14.8:1 ✅ AAA
- Beige `#EFE7D5` sobre Onix `#141414`: ratio ~14.8:1 ✅ AAA

### 2.4 Modo oscuro

La marca **ya opera nativamente en bicromía**, por lo que dark mode no es una "variante" sino una elección de modo. Recomendación:
- **Default = claro (Beige)** — es el modo que mejor encarna la calidez (recepción, papelería, hospitalidad).
- **Dark mode (Onix)** — válido para experiencias inmersivas (galería de fotos, video, contenido editorial).

---

## 3. Tipografía

### 3.1 Familias

| Rol | Fuente | Personalidad | Uso |
|-----|--------|--------------|-----|
| **Display / Titulares** | Calm Serif | Elegancia, tradición | H1, H2, hero, citas, números destacados |
| **UI / Cuerpo** | Montserrat | Cercanía, claridad | Body, labels, botones, navegación, microcopy |

> **Calm Serif** es una serif moderna (display). Si no está disponible vía licencia digital para web, alternativas con personalidad equivalente: **Cormorant Garamond**, **Playfair Display**, **DM Serif Display** (Google Fonts, libres). Validar con marca antes de fallback.

### 3.2 Escala tipográfica (modular, base 16)

```css
:root {
  /* Display — Calm Serif */
  --font-display: "Calm Serif", "Cormorant Garamond", Georgia, serif;
  --text-display-xl: 4.5rem;  /* 72px — hero único */
  --text-display-lg: 3rem;    /* 48px — H1 */
  --text-display-md: 2.25rem; /* 36px — H2 */
  --text-display-sm: 1.75rem; /* 28px — H3 / cita */

  /* UI — Montserrat */
  --font-ui: "Montserrat", -apple-system, "Segoe UI", sans-serif;
  --text-xl:   1.25rem;  /* 20px — H4 / lead */
  --text-lg:   1.125rem; /* 18px — subtítulo */
  --text-base: 1rem;     /* 16px — body (mínimo móvil) */
  --text-sm:   0.875rem; /* 14px — auxiliar */
  --text-xs:   0.75rem;  /* 12px — legales / metadata únicamente */

  /* Pesos */
  --font-weight-regular: 400;
  --font-weight-medium:  500; /* labels, navegación */
  --font-weight-semibold:600; /* botones, énfasis */
  --font-weight-bold:    700; /* sólo titulares cortos */

  /* Line height */
  --lh-tight:  1.15; /* display */
  --lh-snug:   1.35; /* subtítulos */
  --lh-normal: 1.6;  /* body */
  --lh-relaxed:1.75; /* textos largos */

  /* Letter spacing — el logotipo usa tracking generoso ("HOTELES FERRÉ") */
  --tracking-tight:   -0.02em;
  --tracking-normal:  0;
  --tracking-wide:    0.05em;  /* labels, eyebrow */
  --tracking-widest:  0.18em;  /* signature, navegación principal */
}
```

### 3.3 Reglas de uso

- **Calm Serif nunca para body o UI funcional.** Es exclusiva de momentos de marca (hero, cita, número editorial).
- **Montserrat es la fuente del 95% del producto.** Mayúsculas con `tracking-widest` para evocar el logotipo en navegación, eyebrows, footers.
- **Mezcla canónica:** título serif grande + subtítulo Montserrat regular + body Montserrat. Ver portadas y separadores del brandbook.
- **Cursivas Calm Serif** funcionan como acento poético ("*más cerca que nunca*") — usar con moderación.
- Cuerpo mínimo móvil: 16px (regla `readable-font-size` para evitar zoom automático en iOS).
- Medida (line length): 60–75 caracteres en desktop, 35–60 en móvil.

### 3.4 Patrón "headline + cursiva"

El brandbook muestra un patrón distintivo en piezas clave (ej. "Disfruta la **Grandeza** *más cerca que nunca*"):

```
[Verbo de acción en serif regular, tamaño medio]
[SUSTANTIVO PROTAGONISTA en serif grande]
[modificador en cursiva, tamaño medio, con subrayado del acento]
```

Este patrón es **propietario de la marca** y se debe preservar en hero sections de campañas.

---

## 4. Logo y marca gráfica

### 4.1 Anatomía

- **Isotipo:** símbolo "F" estilizado con forma de llama/pluma, trazo de grosor variable.
- **Logotipo:** "HOTELES FERRÉ" en mayúsculas, tracking generoso, serif geométrica.
- **Versiones oficiales:**
  1. Vertical (isotipo arriba + logotipo abajo) — versión principal.
  2. Horizontal (isotipo + logotipo en línea) — para headers/firmas estrechas.
  3. Sólo isotipo — para favicons, avatars, watermarks.
  4. Versión sobre fondo Onix (logo en Beige).

### 4.2 Área de protección

`H = X` (la altura de la "H" del logotipo define el área de respeto en los 4 lados). Ningún elemento debe invadir esta zona.

### 4.3 Tamaños mínimos (recomendación digital)

| Aplicación | Mínimo |
|------------|--------|
| Isotipo en favicon | 32×32px |
| Isotipo en avatar | 48×48px |
| Logo horizontal en header web | 140px de ancho |
| Logo vertical en pieza editorial | 96px de ancho |

### 4.4 Usos incorrectos (anti-patrones — críticos)

❌ Modificar el color de partes del logo
❌ Modificar el color de todo el logo (fuera de las 2 versiones oficiales: Onix y Beige)
❌ Sombras marcadas
❌ Achatar / estirar / distorsionar
❌ Rotar / cambiar orientación (vertical forzada)
❌ Aplicar degradados
❌ Versión a línea (outline)
❌ Modificar tamaño relativo entre isotipo y logotipo
❌ Texturas dentro del logo
❌ Fondos no autorizados (sólo: blanco/Beige, negro/Onix, o fotografía)

> En producto digital: el logo siempre se sirve como SVG con los colores hardcodeados. **No** parametrizar via `currentColor` para evitar usos accidentales no autorizados.

---

## 5. Lenguaje gráfico — el trazo

### 5.1 Principio fundacional

El isotipo no es un símbolo aislado: es la **semilla del sistema gráfico**. Su trazo orgánico de grosor variable se replica en todo punto de contacto, garantizando coherencia.

> *"El trazo nunca es decorativo por sí mismo. Siempre acompaña, guía o resalta — del mismo modo que el servicio humano en Hoteles Ferré: presente, fluido y atento, sin imponerse."*

### 5.2 Aplicaciones del trazo

| Aplicación | Cómo se usa |
|------------|-------------|
| **Contenedor de imágenes** | El trazo forma un marco orgánico que "envuelve" la fotografía. Reemplaza el rectángulo rígido. |
| **Elemento de énfasis** | Subraya frases clave, encierra citas, separa secciones — sin recurrir a cajas. |
| **Iconografía** | Todo set de íconos respeta el principio de grosor variable (no stroke uniforme). |
| **Textura de fondo** | Líneas onduladas que extienden el trazo como atmósfera, no como patrón mecánico. |

### 5.3 Reglas del trazo

1. **Grosor variable, no uniforme.** Un stroke fijo de 2px contradice la marca.
2. **Orgánico, no geométrico.** Curvas Bézier libres, no formas regulares.
3. **Direccional.** Siempre sugiere recorrido o movimiento — nunca cierra completamente como un círculo.
4. **Respira.** Generoso espacio negativo alrededor. Nunca apretado.
5. **Acompaña, no protagoniza.** Si compite con el contenido, está mal usado.

### 5.4 Implementación técnica

- **Formato:** SVG con paths de stroke variable (usar `stroke-width` con gradients o paths rellenos para simular grosor variable).
- **Animación:** ideal para hero/loading — animar `stroke-dashoffset` para dibujar el trazo (200–600ms, ease-out).
- **Respeta `prefers-reduced-motion`:** mostrar trazo estático en vez de animarlo.

### 5.5 Forma "envolvente" (curva sólida)

El brandbook usa una **forma curva sólida en Onix o Beige** que actúa como contenedor de bloques de contenido (ver páginas 4, 13, 16, 17, 23). Es el equivalente de marca a la "card" tradicional.

```css
.ferre-envelope {
  background: var(--color-onix-900);
  color: var(--color-beige-200);
  border-radius: 0; /* la forma viene del path SVG */
  /* Implementar la curva como mask o background-image SVG */
  -webkit-mask-image: url('/assets/envelope-curve.svg');
  mask-image: url('/assets/envelope-curve.svg');
}
```

**Cuándo usar:**
- Hero sections con cita o frase de marca.
- Bloques destacados (testimonios, ofertas, CTAs principales).
- Separadores entre secciones.

**Cuándo NO usar:**
- Cards de listado (uso excesivo banaliza el recurso).
- Botones (los botones siguen siendo rectangulares con border-radius suave).

---

## 6. Iconografía

### 6.1 Sistema

Set propietario derivado del trazo del logotipo. Ejemplos del brandbook: taxi/ubicación, teléfono, no fumar, gimnasio, secadora, llave, room service, equipaje, café, candado, tarjeta, piscina.

### 6.2 Especificaciones

| Atributo | Valor |
|----------|-------|
| **Estilo** | Lineal con grosor variable (no uniforme) |
| **Color** | Beige sobre fondo Onix, o Onix sobre fondo Beige (nunca mezclar) |
| **Esquinas** | Redondeadas suavemente, nunca afiladas |
| **Trazo** | Variable, orgánico, abierto (no siempre cerrado) |
| **Tamaños** | 16, 20, 24, 32, 48px (escala de tokens) |
| **Touch target** | Mínimo 44×44pt incluyendo padding, aunque el ícono visual sea de 24px |

### 6.3 Reglas

- **Prohibido el emoji como ícono estructural** (regla `no-emoji-icons`). Sólo SVG propietarios.
- **No mezclar** outline + filled en la misma jerarquía.
- **No** sustituir el set por librerías genéricas (Heroicons, Material Icons) sin pasar por marca. Si se necesita un ícono no existente, encargar al equipo de diseño que lo cree respetando el principio de grosor variable.

---

## 7. Fotografía

### 7.1 Filosofía

> *"La fotografía no busca impresionar, busca hacer sentir."*

Cada imagen comunica reconocimiento humano, calma y elegancia sin rigidez. Es **documental antes que comercial**.

### 7.2 Lineamientos técnicos

| Atributo | Especificación |
|----------|----------------|
| **Iluminación** | Luz natural o simulación muy suave. No flash duro. |
| **Color** | Cálidos, contrastes bajos, sombras suaves |
| **Composición** | Limpia, sin saturación visual |
| **Edición** | Mínima. Evitar filtros agresivos, HDR, sharpening excesivo |
| **Saturación** | Ligeramente desaturada, nunca neón |
| **Grano** | Aceptable y deseable en piezas editoriales (suma autenticidad) |

### 7.3 Tipos de toma (tier list)

**✅ Tier 1 — Esenciales:**
- Recepción con contacto visual real (miradas, sonrisas contenidas, saludo).
- Detalles humanos: una mano sirviendo café, una maleta cuidada, una puerta abriéndose.
- Habitaciones con luz natural, ligeramente vividas (cortinas movidas, cama abierta).
- Equipo humano **en acción**, nunca posando rígido.

**⚠️ Tier 2 — Con criterio:**
- Contexto local sutil (luz, textura, paisaje insinuado). **No postal turística.**
- Huéspedes interactuando con la experiencia (desayuno, brindis, lectura).

**❌ Anti-patrones fotográficos:**
- Stock photography genérica (sonrisas perfectas, fondos blancos, modelos).
- Fotos con flash directo, fondos saturados.
- Composiciones simétricas perfectas y "publicitarias".
- Drones turísticos de Machu Picchu sin recurso de marca que los integre.
- Personas posando frontalmente al lente.

### 7.4 Tratamiento en producto

- **Marco:** las fotos se "envuelven" con el trazo orgánico (ver §5.2). Los rectángulos rígidos son anti-patrón salvo en contextos puramente funcionales (galería de admin, miniaturas de listado denso).
- **Aspect ratios preferidos:** 4:5 (vertical), 3:2 (horizontal), 1:1 (cuadrado para sociales). Evitar 16:9 panorámico salvo video.
- **Optimización:** WebP/AVIF, responsive `srcset`, lazy loading bajo el fold (regla `image-optimization`). Reservar espacio con `aspect-ratio` para evitar CLS.

---

## 8. Layout, espaciado y forma

### 8.1 Filosofía de layout

- **Generoso.** El brandbook es deliberadamente espacioso. La densidad es enemiga de la elegancia.
- **Asimetrías controladas.** Las páginas del brandbook combinan bloques rectos con curvas envolventes — esa tensión es marca.
- **Ritmo vertical claro.** Las separaciones entre secciones son grandes (48–96px en desktop).

### 8.2 Sistema de espaciado (escala 4/8)

```css
--space-1:  0.25rem;  /*  4px */
--space-2:  0.5rem;   /*  8px */
--space-3:  0.75rem;  /* 12px */
--space-4:  1rem;     /* 16px */
--space-5:  1.5rem;   /* 24px */
--space-6:  2rem;     /* 32px */
--space-7:  3rem;     /* 48px */
--space-8:  4rem;     /* 64px */
--space-9:  6rem;     /* 96px */
--space-10: 8rem;     /* 128px — separador entre secciones grandes */
```

### 8.3 Border radius

```css
--radius-sm:  4px;   /* inputs */
--radius-md:  8px;   /* botones, chips */
--radius-lg:  16px;  /* cards */
--radius-xl:  24px;  /* contenedores destacados */
--radius-full:9999px;/* avatares, pills */
```

> **Importante:** las "envolventes" curvas características de la marca (ver §5.5) **no** son `border-radius`, son SVG masks. No intentar replicarlas con CSS puro.

### 8.4 Sombras

> El brandbook prohíbe sombras marcadas en el logo, y el espíritu se extiende al producto.

```css
--shadow-none: none;
--shadow-sm:   0 1px 2px rgba(20, 20, 20, 0.04);
--shadow-md:   0 4px 12px rgba(20, 20, 20, 0.06);
--shadow-lg:   0 12px 32px rgba(20, 20, 20, 0.08);
```

Sombras siempre sutiles, basadas en Onix con baja opacidad. **Nunca sombras negras puras de alta opacidad** — rompen la calidez.

### 8.5 Breakpoints

```css
--bp-sm:  640px;  /* móvil grande */
--bp-md:  768px;  /* tablet */
--bp-lg:  1024px; /* desktop */
--bp-xl:  1280px; /* desktop amplio */
--bp-2xl: 1536px; /* hero/wide */
```

Mobile-first. Container máximo `max-width: 1280px` con gutters adaptativos (16px móvil → 32px desktop → 48px wide).

---

## 9. Componentes — guía de aplicación

### 9.1 Botones

| Variante | Fondo | Texto | Uso |
|----------|-------|-------|-----|
| **Primary** | `--color-onix-900` | `--color-beige-200` | CTA principal (1 por pantalla) |
| **Secondary** | transparent + border `--color-onix-900` | `--color-onix-900` | Acción secundaria |
| **Ghost** | transparent | `--color-onix-700` | Acciones terciarias, links |
| **Inverse** | `--color-beige-200` | `--color-onix-900` | Sobre fondo Onix |

```css
.btn {
  font-family: var(--font-ui);
  font-weight: var(--font-weight-semibold);
  letter-spacing: var(--tracking-wide);
  text-transform: uppercase;
  font-size: var(--text-sm);
  padding: 14px 28px;
  border-radius: var(--radius-md);
  min-height: 44px; /* touch target */
  transition: all 200ms ease-out;
}

.btn-primary:hover {
  background: var(--color-onix-700);
  /* Nunca cambiar de color a uno saturado en hover */
}
```

**Reglas:**
- Una sola CTA primaria por vista (regla `primary-action`).
- Estados visibles: hover, focus (anillo de 2px en Onix con offset), active, disabled, loading.
- Nunca usar emoji ni íconos genéricos en botones (regla `no-emoji-icons`).

### 9.2 Cards

```css
.card {
  background: var(--color-beige-200);
  border-radius: var(--radius-lg);
  padding: var(--space-6);
  box-shadow: var(--shadow-md);
  border: 1px solid var(--border-subtle);
}
```

Para cards "marca" (testimonios, citas, destacados): usar la forma envolvente SVG (§5.5) en lugar del rectángulo.

### 9.3 Forms / Inputs

```css
.input {
  font-family: var(--font-ui);
  font-size: var(--text-base); /* 16px mínimo, evita zoom iOS */
  padding: 12px 16px;
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-sm);
  background: var(--color-beige-100);
  min-height: 44px;
}

.input:focus {
  outline: 2px solid var(--color-onix-900);
  outline-offset: 2px;
  border-color: var(--color-onix-900);
}
```

**Reglas:**
- Label visible siempre (regla `form-labels`). Nunca label-en-placeholder.
- Mensajes de error junto al campo, no agrupados al final.
- Helper text por defecto, error solo en estado de error.

### 9.4 Navegación

- **Web desktop:** logo a la izquierda, navegación horizontal centrada/derecha en Montserrat con `tracking-widest` en mayúsculas, idioma+CTA reserva al extremo derecho.
- **Web móvil:** logo + hamburguesa. Drawer slide-in con curva envolvente de marca.
- **App nativa:** bottom nav (≤5 ítems, regla `bottom-nav-limit`) con íconos del set propietario + label corto.

### 9.5 Modales / Sheets

- Scrim Onix al 60% (`rgba(20, 20, 20, 0.6)`) — regla `scrim-and-modal-legibility`.
- Cierre siempre visible (X superior derecha + tap en scrim).
- Animación de entrada: 280ms ease-out, salida 180ms (regla `exit-faster-than-enter`).

---

## 10. Movimiento y animación

### 10.1 Principios

El movimiento extiende la metáfora del trazo: **fluido, presente, atento, sin imponerse.**

| Atributo | Valor |
|----------|-------|
| **Duración micro-interacción** | 150–250ms |
| **Duración transición de página** | 280–400ms |
| **Easing entrada** | `cubic-bezier(0.22, 1, 0.36, 1)` (ease-out suave) |
| **Easing salida** | `cubic-bezier(0.4, 0, 1, 1)` (ease-in) |
| **Preferencia** | Spring physics sobre easings lineales para feel orgánico |
| **Salida vs entrada** | Salida ~60–70% de la duración de entrada |

### 10.2 Animaciones recomendadas

- **Hero:** trazo del isotipo dibujándose con `stroke-dashoffset` (400–600ms).
- **Hover en cards:** elevación sutil (shadow-md → shadow-lg) + leve translateY(-2px). Sin escalado agresivo.
- **Listas:** stagger de 30–50ms por ítem en entrada.
- **Página → página:** crossfade + slide horizontal de 24px.

### 10.3 Anti-patrones

- ❌ Animaciones decorativas sin propósito.
- ❌ Parallax pesado (rompe la sobriedad).
- ❌ Bounces exagerados (rompen el tono "elegante").
- ❌ Cualquier animación que no respete `prefers-reduced-motion`.

---

## 11. Microcopy y voz en producto

### 11.1 Reglas

1. **Anfitrión, no anunciante.** "Lo esperamos" > "Reserve ahora".
2. **Usar nombres, momentos y detalles.** "Su habitación con vista al valle está lista" > "Habitación confirmada".
3. **Evitar superlativos vacíos.** Eliminar "experiencias inolvidables", "el mejor servicio", "lujo total".
4. **Honestidad antes que promesa.** Si algo puede tardar, decirlo.
5. **Formal sin ser frío.** Usted (no tú), pero conversacional.

### 11.2 Vocabulario marca

| ✅ Preferir | ❌ Evitar |
|-------------|-----------|
| Anfitrión / acompañar | Atención al cliente |
| Estadía | Hospedaje |
| Huésped | Cliente / usuario |
| Le esperamos / lo recibimos | Confirmamos su transacción |
| Costa, Sierra, Selva | Destinos / locaciones |
| Detalle / cuidado | Beneficio / feature |

### 11.3 Hashtag y firma

- Firma de marca observada en piezas: *"Donde cada instante se vive mejor."*
- Tono campaña: *"Disfruta la **Grandeza** más cerca que nunca"* (estructura headline §3.4).
- En sociales: hablar como anfitrión, usar nombres reales del equipo y huéspedes (con permiso).

---

## 12. Redes sociales

### 12.1 Rol

Las redes **no venden habitaciones, construyen confianza**. Extienden la experiencia Ferré antes, durante y después de la estadía.

### 12.2 Pilares de contenido

1. **Experiencias locales** (Costa/Sierra/Selva, no postal turística).
2. **Equipo humano** (rostros, oficios, momentos).
3. **Detalles que importan** (un café servido, una toalla doblada, una vista).

### 12.3 Plantillas visuales

| Tipo | Reglas |
|------|--------|
| **Post (1:1 / 4:5)** | Foto domina. Si hay texto, mínimo: 1 título serif + máximo 1 elemento gráfico (trazo). Sin grafismo recargado. |
| **Story / Reel cover (9:16)** | Foto domina. Texto reducido al mínimo. Tipografía de marca obligatoria. |
| **Carrusel** | Primera tarjeta = hook visual sin sobreinformación. Tarjetas siguientes pueden ser más informativas pero respetando jerarquía. |
| **Video vertical** | Sin gráficos sobrecargados. Un título + máximo un recurso gráfico (trazo). Subtítulos en Montserrat. |

### 12.4 Ejemplos de campañas (extraídos del brandbook)

- *"Es momento de **Disfrutar** experiencias"*
- *"3 lugares que no conocías en **Cuzco**"*
- *"Disfruta la **Grandeza** más cerca que nunca"*
- *"Servicio de **Primera**"*
- *"**Desayuno** Buffet"*
- *"Donde cada instante se vive mejor."* (firma)

Patrón observado: **verbo o número en serif regular + sustantivo protagonista en serif mayor + acento en cursiva.**

---

## 13. Papelería y aplicaciones físicas

> *Sobriedad. Materiales nobles. Diseño funcional. Cada objeto físico refuerza la percepción de cuidado y orden.*

| Pieza | Especificaciones clave |
|-------|------------------------|
| **Hoja membretada** | Fondo beige, isotipo + logo arriba derecha, bloque "Para:" con curva envolvente Onix, footer con datos de contacto + ícono trazado |
| **Tarjeta presentación** | Bicromía: cara Onix con isotipo+logo en Beige, cara Beige con datos en Onix |
| **Carpeta / portafolios** | Onix, isotipo + logo grandes centrado |
| **Door hangers** | Bicromía Onix/Beige, mensaje en Calm Serif cursiva ("Please, do not disturb" / "Please, make up the room"), trazo decorativo discreto |
| **Notebook / agenda** | Onix con isotipo en Beige centrado, lomo limpio |

**Materiales recomendados:** papel texturizado mate (no satinado / glossy), gramaje alto (350g+ para tarjetas), tintas pantone para Onix y Beige, sin barnices brillantes.

---

## 14. Accesibilidad — checklist no negociable

- [ ] Contrastes texto ≥ 4.5:1 (AAA cuando posible — la bicromía Onix/Beige cumple holgado).
- [ ] Touch targets ≥ 44×44pt en todos los controles tappables.
- [ ] Foco visible siempre (anillo Onix 2px con offset).
- [ ] `alt` descriptivo en todas las imágenes con valor de marca.
- [ ] `aria-label` en botones de sólo ícono.
- [ ] Jerarquía heading secuencial (h1 → h6, sin saltos).
- [ ] Color nunca es la única vía de información (estados acompañados de ícono + texto).
- [ ] `prefers-reduced-motion` respetado (animaciones del trazo se vuelven estáticas).
- [ ] Soporte de Dynamic Type / zoom de texto sin truncamientos.
- [ ] Forms con labels visibles y errores adyacentes al campo.
- [ ] Navegación por teclado en orden visual.

---

## 15. Anti-patrones — qué nunca hacer

### Marca
- ❌ Introducir un tercer color de marca sin aprobación.
- ❌ Usar negro puro `#000` o blanco puro `#FFF` como fondo.
- ❌ Modificar el logo (ver §4.4 — 11 anti-patrones explícitos).
- ❌ Usar emoji como ícono estructural.
- ❌ Stock photography genérica.
- ❌ Tipografías fuera del sistema (Calm Serif + Montserrat).

### UX
- ❌ "Reserve ahora" agresivo / countdowns de urgencia falsa.
- ❌ Pop-ups intrusivos al primer scroll.
- ❌ Lenguaje transaccional frío.
- ❌ Densidad alta de información (rompe "menos es más").
- ❌ Animaciones decorativas que no aportan significado.
- ❌ Contrastes débiles (Beige claro sobre Beige base, etc.).

### Comunicación
- ❌ Lenguaje corporativo vacío ("nos comprometemos a brindar...").
- ❌ Frases genéricas de hotelería ("su hogar lejos de casa" — usado pero ya gastado, ver bio Instagram).
- ❌ Promesas exageradas ("la mejor experiencia de su vida").
- ❌ Tuteo cuando contradice el tono "anfitrión sofisticado".

---

## 16. Roadmap de implementación digital

### Fase 1 — Fundamentos (semanas 1–2)
1. Tokenizar colores, tipografía, espaciado en CSS variables / Tailwind config / theme nativo.
2. Configurar fuentes (licenciar Calm Serif para web; Montserrat vía Google Fonts con `font-display: swap`).
3. Exportar SVG oficiales del logo (3 variantes × 2 colores = 6 archivos).
4. Crear set de íconos base (12–24 esenciales) respetando grosor variable.

### Fase 2 — Componentes (semanas 3–4)
1. Botones (4 variantes × 5 estados).
2. Cards (estándar + envolvente de marca).
3. Inputs / forms con validación.
4. Navegación (header web + bottom nav app).
5. Modales / sheets con scrim correcto.

### Fase 3 — Páginas plantilla (semanas 5–6)
1. Landing / homepage con hero animado del trazo.
2. Página de hotel (Costa/Sierra/Selva) con galería envolvente.
3. Flujo de reserva (3–4 pasos) con microcopy de marca.
4. Confirmación / "thank you" como momento de marca.

### Fase 4 — QA y refinamiento (semana 7)
1. Auditoría de accesibilidad (Lighthouse, axe).
2. Test de rendimiento (Core Web Vitals, CLS < 0.1).
3. Test en dispositivos reales (móvil pequeño 375px, tablet, desktop wide).
4. Validación con stakeholders de marca.

---

## 17. Glosario

| Término | Significado |
|---------|-------------|
| **Onix** | Color oscuro de marca (≈ `#141414`). No es negro puro. |
| **Beige** | Color claro de marca (≈ `#EFE7D5`). No es blanco puro. |
| **Trazo** | Lenguaje gráfico orgánico de grosor variable, derivado del isotipo. |
| **Envolvente** | Forma curva sólida (Onix o Beige) que actúa como contenedor de marca. |
| **Bicromía** | Sistema de dos colores estricto (Onix + Beige) sin terceros tonos saturados. |
| **Cuidador Sofisticado** | Arquetipo de marca: educado, firme, protector, cercano sin informalidad. |

---

## 18. Referencias y siguiente paso

- **Brandbook fuente:** `Brandbook_ferre_2026_v4-compressed.pdf`
- **Validación pendiente con marca:** valores HEX exactos de Onix y Beige, licencia digital de Calm Serif, archivo maestro del set de íconos en SVG.
- **Tokens recomendados a generar:** `tokens.css`, `tailwind.config.js`, `theme.json` (nativo).

> Este documento es la fuente única de verdad para el diseño digital de Hoteles Ferré. Cualquier desviación debe documentarse y aprobarse por el equipo de marca.
