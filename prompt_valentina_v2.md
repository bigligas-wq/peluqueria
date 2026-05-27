# PROMPT — VALENTINA PEINADOS · Landing Page v2

> Pegá este prompt en Claude.ai con TODAS las fotos subidas al proyecto con estos nombres exactos:
> `cartel-noche.jpg` · `modelo-rubia.jpg` · `modelo-morena.jpg` · `botella-valentina.jpg` · `extensiones.jpg`

---

Sos el mejor diseñador y desarrollador web del mundo. Tu trabajo hoy es crear la landing page definitiva para **VALENTINA — Get the look**, una peluquería premium con 35 años de historia en Olavarría, Argentina.

Este es el producto real, funcional y escalable desde el primer commit. El código tiene que estar tan bien estructurado que cualquier desarrollador pueda abrir el archivo y seguir construyendo encima sin reescribir nada. Variables CSS organizadas en `:root`, secciones comentadas, JS organizado en funciones nombradas. Base sólida para crecer.

Las fotos están subidas al proyecto con estos nombres exactos — usálas todas con `<img>` directamente:
- `cartel-noche.jpg` → el cartel retroiluminado de noche con spotlights dramáticos (HERO)
- `modelo-rubia.jpg` → mujer rubia de espaldas frente al cartel, luz cálida diurna
- `modelo-morena.jpg` → mujer morena de espaldas frente al cartel, ambiente oscuro dramático
- `botella-valentina.jpg` → mano sosteniendo botella ámbar VALENTINA, sombra de hojas sobre fondo cálido
- `extensiones.jpg` → mano sosteniendo extensiones con etiqueta EXTENSIONS, sombra de hojas

No las reemplaces por nada. Son fotografías profesionales reales y son el alma de la página.

---

## DIRECCIÓN DE DISEÑO

**Concepto:** Editorial de lujo silencioso. Como si Vogue Argentina diseñara el sitio de un salón de Palermo Soho. Todo lo que se mueve, se mueve con intención. Todo lo que está quieto, está quieto con confianza.

**Lo que NO es esto:** No tiene gradientes morados. No tiene sombras gris genéricas. No tiene cards con border-radius de 16px. No usa Inter ni Roboto ni Space Grotesk. No tiene ese aspecto de "lo hizo una IA en 5 minutos". No recargado. No burbuja.

**Lo que SÍ es esto:** Blanco cálido. Negro profundo. Verde oscuro como un filo. Tipografía que ocupa espacio y lo merece. Fotos que respiran. Animaciones que sorprenden una vez y no molestan después.

---

## SISTEMA DE DISEÑO

**Paleta — definir como variables CSS:**
```css
:root {
  --blanco:       #FAFAF8;
  --negro:        #0A0A0A;
  --verde:        #1B4D35;
  --verde-hover:  #246642;
  --oro:          #C9A96E;   /* solo líneas decorativas finas */
  --gris-texto:   #6B6B6B;
  --fondo-oscuro: #0F0F0F;
  --fondo-card:   #F2F2EF;
}
```

**Tipografía — importar de Google Fonts:**
- `Cormorant Garamond` (300, 400, 600, 700 italic) → títulos grandes, citas, números decorativos
- `Jost` (300, 400, 500) → navegación, body, labels, botones
- `Pinyon Script` (400) → exclusivamente para "Get the look" y detalles script

**Reglas tipográficas:**
- Hero title: Cormorant Garamond 300, mínimo 130px desktop, tracking 0.08em
- Títulos de sección: Cormorant Garamond, 56–72px
- Body: Jost 300, 16px, line-height 1.7
- Botones: Jost 500, 12px, uppercase, tracking 0.18em
- Eyebrow labels: Jost 400, 11px, uppercase, tracking 0.25em

---

## ESTRUCTURA — sección por sección

### INTRO ANIMATION
Pantalla negra completa al cargar. En el centro: las letras de "VALENTINA" aparecen una por una desde el centro con stagger de 70ms cada una (cada letra es un `<span>`, animación: `opacity 0→1` + `translateY(20px→0)`, 500ms ease-out). Cuando termina la última letra, aparece "— Get the look —" en Pinyon Script verde deslizándose suavemente desde abajo (translateY 15px→0, 600ms ease-out, 200ms delay después de la última letra). Luego de 0.8s de pausa: fade out de toda la pantalla intro (opacity 1→0, 500ms). Guardar en `sessionStorage.setItem('intro', 'done')` para no repetir en navegación interna.

### NAVBAR
Fija top. Altura 72px. Fondo: `transparent` sobre el hero → `rgba(10,10,10,0.95)` con `backdrop-filter: blur(16px)` al scrollear más de 60px. Transición 400ms ease. Borde inferior: `1px solid rgba(255,255,255,0.06)` solo en estado scrolled.

Izquierda: logo en CSS — "VALENTINA" Cormorant Garamond 600 blanco tracking 0.06em + debajo "Get the look" Pinyon Script 18px verde.
Derecha (desktop): links Jost 11px uppercase tracking 0.2em blanco 70% · "Servicios" · "Turnos" · "Tienda" · botón [RESERVAR] con fondo verde, texto blanco, padding 10px 24px, border-radius 3px, hover fondo verde-hover con transición 250ms.
Mobile: hamburger (3 líneas blancas → X animado al abrir). Al abrir: overlay negro 100vh con los links centrados en Cormorant 40px. Se cierra con la X o al hacer click en un link.

### SECCIÓN 1 — HERO
Fondo: `cartel-noche.jpg`, full screen, `object-fit: cover`, `object-position: center`. Overlay `rgba(0,0,0,0.38)`.

**Parallax:** el fondo se mueve a 40% de la velocidad del scroll con `transform: translateY()` + `requestAnimationFrame`.

Contenido centrado verticalmente con `position: absolute`:
- Eyebrow: Jost 11px uppercase tracking 0.3em, blanco 55% opacidad — "OLAVARRÍA · DESDE 1989"
- "VALENTINA" — Cormorant Garamond 300, 130px desktop, blanco, tracking 0.08em. Cada letra es un `<span>`, entran con stagger 50ms desde abajo (translateY 30px→0 + opacity 0→1) al cargar la página (después del intro).
- "— Get the look —" — Pinyon Script, 52px, color verde `#1B4D35`, entra 400ms después con fade + translateY.
- Subtítulo: Jost 300, 17px, blanco 80%, "Especialistas en colorimetría. 35 años siendo el salón elegido."
- Dos botones con gap 16px:
  - [RESERVAR TURNO] — borde blanco 1px, fondo transparente, texto blanco. Hover: fondo blanco, texto negro. Transición 300ms.
  - [VER PRODUCTOS] — solo texto blanco, con una línea horizontal animada debajo que se expande de 0 a 100% en hover.
- Scroll indicator: línea vertical blanca de 40px que pulsa suavemente (animation: pulse 2s infinite), texto "scroll" en Jost 10px rotado 90° al lado.

### SECCIÓN 2 — MARQUEE STRIP
Franja oscura `#0F0F0F`, altura 52px, overflow hidden. Texto infinito en loop que corre de derecha a izquierda — Jost 11px uppercase tracking 0.3em, blanco 40%:
`VALENTINA · GET THE LOOK · COLORIMETRÍA · BALAYAGE · EXTENSIONES · ALISADO PREMIUM · OLAVARRÍA · DESDE 1989 · QUESTIONI PROFESSIONAL ·`
Velocidad: 30s linear infinite. Sin pausa en hover.

### SECCIÓN 3 — STATEMENT (solo tipografía)
Fondo: `#FAFAF8`. Padding vertical 180px arriba y abajo.

Solo texto, centrado:
- Cita en Cormorant Garamond italic 68px, negro, line-height 1.1:
  *"No solo te peinamos."*
  (pausa de 0.3em entre líneas)
  *"Te transformamos."*
- Línea horizontal `#C9A96E` de 48px, 1px alto — **se dibuja de izquierda a derecha** con animación CSS: `width: 0 → 48px`, 800ms ease-out al entrar en viewport.
- Subtexto Jost 300 16px gris: "Desde 1989, cada clienta que entra sale siendo la mejor versión de sí misma."

**Efecto de scroll:** `clip-path: inset(0 100% 0 0) → inset(0 0% 0 0)` en el contenedor completo al entrar en viewport — el texto se revela como si corriera un telón de derecha a izquierda. 900ms cubic-bezier(0.77, 0, 0.175, 1).

### SECCIÓN 4 — GALERÍA EDITORIAL
Fondo: `#FAFAF8`.

Título alineado izquierda antes del grid: "El trabajo habla." Cormorant Garamond 64px negro. Entra con el efecto clip-path lateral igual que la sección anterior.

Layout **CSS Grid** asimétrico, 3 columnas, alturas variables — editorial tipo revista. Cada foto con `overflow: hidden`:

```
Área desktop (grid-template-areas):
"grande  mediana  cuadrada"
"grande  vertical vertical"
"banner  banner   banner  "
```

- **grande** (2 filas alto, columna izquierda): `modelo-morena.jpg` — la morena dramática. Entrada: `translateX(-60px) opacity 0 → translateX(0) opacity 1`, 800ms.
- **mediana** (arriba derecha): `modelo-rubia.jpg` — la rubia diurna. Entrada: `translateY(-40px) opacity 0 → normal`, 700ms delay 150ms.
- **cuadrada** (arriba centro): `botella-valentina.jpg` — objeto de deseo. Entrada: `scale(0.92) opacity 0 → scale(1) opacity 1`, 700ms delay 100ms.
- **vertical** (abajo derecha): `extensiones.jpg` — vertical. Entrada: `translateX(60px) opacity 0 → normal`, 800ms delay 200ms.
- **banner** (última fila, ancho total): `cartel-noche.jpg` — el cartel retroiluminado como cierre de sección. Altura 320px. `object-fit: cover`, `object-position: center 30%`. Entrada: `scale(0.96) opacity 0 → scale(1) opacity 1`, 1000ms delay 100ms.

Todas las imágenes al hover: `transform: scale(1.05)` en el `<img>` interior, 700ms ease. Sin bordes. Sin sombras. Las fotos hablan solas.

Cada imagen tiene su propia velocidad de parallax sutil (JS IntersectionObserver + getBoundingClientRect):
- modelo-morena: factor 0.08
- botella-valentina: factor 0.12
- extensiones: factor 0.10
- banner: factor 0.05

### SECCIÓN 5 — CONTADOR DE IMPACTO
Fondo: `#0F0F0F`. Padding 100px vertical.

3 columnas centradas con números que **cuentan desde 0 al valor final** con easing cuando entran en viewport (JS con requestAnimationFrame + easeOutQuart):

```
35          +3000         8.8
AÑOS        CLIENTAS      PUNTUACIÓN
DE HISTORIA ATENDIDAS     PROMEDIO
```

Números en Cormorant Garamond 300, 96px, blanco. Texto debajo en Jost 11px uppercase tracking ancho, verde `#1B4D35`. Separados por líneas verticales `1px solid rgba(255,255,255,0.12)`.

Entrada al scroll: cada columna con `translateY(30px) opacity 0 → normal`, stagger 150ms entre ellas.

### SECCIÓN 6 — SERVICIOS
Fondo: `#0F0F0F`.

Título en blanco: "Lo que hacemos" — Cormorant Garamond 64px, alineado izquierda. Línea verde `2px` de 56px debajo, que se dibuja al entrar (igual que la línea dorada de la sección statement pero en verde).

Seis servicios en lista elegante. Cada fila:
- Separador top: `1px solid rgba(255,255,255,0.08)`
- Número `01`–`06` en Cormorant 96px, `rgba(255,255,255,0.04)`, `position: absolute`, no interactúa con el layout
- Nombre en Cormorant bold 32px blanco
- Descripción Jost 300 14px `#6B6B6B`
- Duración Jost 11px uppercase verde, alineado derecha
- Flecha `→` en verde que aparece con `translateX(-8px) → translateX(0) opacity 0 → 1` solo en hover

Al hover en cada fila: `background: rgba(27,77,53,0.1)`, la línea separadora top cambia a verde, transición 350ms. La fila completa se "activa".

Entradas con stagger: cada fila entra con `translateY(25px) opacity 0 → normal` con delay escalonado de 80ms.

```
01 · Cama Solar Miami Sun
     "Única en Olavarría. Bronceado natural en 15 minutos."
     15 min

02 · Colorimetría & Balayage
     "Especialidad de la casa desde hace 35 años. Traé referencia, hacemos el resto."
     Desde 90 min

03 · Alisado Premium
     "Sin parabenos, libre de formol. El precio varía según largo y cantidad."
     120 min

04 · Extensiones
     "Largo y volumen naturales. Las mejores extensiones del mercado."
     A convenir

05 · Keratina en Spray
     "Hidratación, brillo y suavidad profesional. Resultado inmediato."
     60 min

06 · Corte & Peinado
     "Para el día a día o tu evento más especial."
     45 min
```

### SECCIÓN 7 — RESERVAR TURNO
Fondo: `#FAFAF8`.

Layout dos columnas 50/50 en desktop:

**Columna izquierda:** `modelo-morena.jpg`, altura completa de la sección, `object-fit: cover`. Sin texto encima. Entrada: `clip-path: inset(0 0 100% 0) → inset(0 0 0% 0)`, 1000ms cubic-bezier(0.77, 0, 0.175, 1) — la foto se revela de arriba hacia abajo como una cortina.

**Columna derecha:** padding 80px 64px.
- Eyebrow verde Jost uppercase: "RESERVAS"
- Título Cormorant 56px negro: "Reservá tu turno"
- Subtítulo Jost 300: "Completá el formulario y te confirmamos por mail en minutos."

Formulario — inputs con **solo línea inferior** (`border: none; border-bottom: 1px solid #D0D0D0`), fondo transparente, sin border-radius:
```
Nombre completo *
Teléfono *
Email *
Servicio (select estilizado, flecha custom en verde)
Fecha preferida (date input estilizado)
Mensaje opcional (textarea 3 líneas)
```

Labels: Jost 11px uppercase tracking 0.2em verde, sobre el input.
Focus: la línea inferior cambia a verde `#1B4D35`, transición 300ms.
Placeholder: Jost 300, gris claro.

Botón [CONFIRMAR TURNO]: ancho 100%, altura 52px, fondo verde `#1B4D35`, texto blanco Jost uppercase tracking 0.15em, border-radius 2px. Hover: verde-hover `#246642`, transición 250ms.

Al submit (sin backend — la estructura está lista para conectar): el formulario hace `opacity 0` + `translateY(-10px)` con fade, aparece centrado: checkmark SVG animado (stroke-dashoffset de 100% a 0%, 600ms ease) en verde + "Turno recibido. Te contactamos a la brevedad." en Cormorant italic 28px verde.

### SECCIÓN 8 — TIENDA
Fondo: `#FAFAF8`.

Eyebrow verde: "TIENDA"
Título Cormorant 64px: "Nuestra Tienda"
Subtítulo Jost: "Productos profesionales que usamos y recomendamos."

Grid de 3 columnas desktop. El producto estrella es más alto (grid-row: span 2 o simplemente más padding).

**Producto estrella — usar `botella-valentina.jpg`:**
- Imagen cuadrada top, ocupa el espacio predominante
- Nombre: "Elixir Capilar Valentina" — Cormorant 26px
- Descripción: "Fórmula exclusiva del salón. Brillo, hidratación y protección duradera." — Jost 300 14px
- Precio: "$8.500"
- Botón [COMPRAR POR WHATSAPP] → abre `https://wa.me/5492284429469?text=Hola! Me interesa el Elixir Capilar Valentina` en nueva pestaña

**2 productos adicionales de ejemplo** (usar estas URLs exactas de Unsplash):
```
Máscara Nutrición Profunda · $6.200
https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?w=600&q=80

Spray Brillo Profesional · $4.800
https://images.unsplash.com/photo-1571781926291-c477ebfd024b?w=600&q=80
```

Cards: imagen top `object-fit: cover`, nombre Cormorant, precio Jost, botón borde verde 1px texto verde. Hover: imagen hace `scale(1.04)` (overflow hidden en card), borde card cambia a verde, sombra `0 8px 32px rgba(27,77,53,0.12)`. Transición 400ms ease.

Entrada al scroll: cada card con `translateY(40px) opacity 0 → normal`, stagger 120ms.

### SECCIÓN 9 — FOOTER
Fondo: `#0A0A0A`.

Línea decorativa verde `2px solid #1B4D35` en el top, que se dibuja de izquierda a derecha al entrar en viewport.

Layout 3 columnas con gap:
- **Col 1:** Logo en CSS blanco grande. Tagline Jost 300 gris: "El salón elegido de Olavarría."
- **Col 2:** Jost 300 gris, line-height 2:
  Vicente López 3175, Olavarría, Buenos Aires
  Mar–Sáb · 9:00 — 18:00 hs
  Lunes y Domingo cerrado
- **Col 3:** Instagram @valentinapeinados · Tel (0228) 442-9469 · Link "Reservar turno" con underline verde

Línea separadora `1px solid rgba(255,255,255,0.08)`.
Copyright: `© 2026 Valentina Peinados · Sitio desarrollado por blstudio` — "blstudio" en verde es un link `https://stgrandesligas.com` que abre en nueva pestaña.

---

## EFECTOS Y ANIMACIONES — implementar todos

### 1. Scroll Reveal con clip-path (efecto telón)
Para los títulos de sección y bloques de texto importantes — no solo translateY. Usar `clip-path: inset(0 0 100% 0) → inset(0 0 0% 0)` para revelar el texto como si cayera de arriba. Para columnas que vienen del costado usar la variante horizontal. IntersectionObserver con threshold 0.2.

### 2. Parallax hero
JS puro con `requestAnimationFrame`. `scrollY * 0.4` aplicado como `translateY` al `background-position` del hero.

### 3. Parallax individual en galería
Cada imagen en la galería tiene un factor de parallax diferente (entre 0.05 y 0.12) calculado con `getBoundingClientRect().top` en el evento scroll. Efecto sutil, no exagerado.

### 4. Marquee
CSS `@keyframes` con `translateX(0) → translateX(-50%)` en `linear infinite`. Duplicar el contenido del marquee para que sea seamless.

### 5. Contador animado
Función JS que recibe (elemento, valorFinal, duración). Usa `requestAnimationFrame` con easing `easeOutQuart`. Se dispara cuando el elemento entra en viewport (IntersectionObserver, una sola vez).

### 6. Línea que se dibuja
Línea dorada y líneas verdes decorativas: ancho empieza en `0`, al entrar en viewport hace transición CSS a su ancho final. `transition: width 900ms cubic-bezier(0.25, 0.46, 0.45, 0.94)`.

### 7. Navbar scroll
`scroll` event listener. A los 60px: añadir clase `.scrolled` al navbar. Clase `.scrolled` activa el fondo oscuro con blur.

### 8. Línea de progreso de scroll
`<div id="progress">` fijo en top, altura 2px, fondo verde `#1B4D35`, z-index 9998, width calculado como `(scrollY / (documentHeight - windowHeight)) * 100%`. Actualizar en RAF.

### 9. Cursor personalizado (solo desktop, `pointer: fine`)
`<div id="cursor">` — círculo 14px, borde 1.5px sólido verde, `position: fixed`, `pointer-events: none`, z-index 9997. Interpolación suave: `currentX += (targetX - currentX) * 0.12` en RAF. Al hacer hover sobre `a, button`: escala 2.5x + `background: rgba(27,77,53,0.1)` con transición 200ms.

### 10. Grain texture
`body::after` con SVG de ruido en base64 inline como background, `opacity: 0.022`, `position: fixed`, `inset: 0`, `pointer-events: none`, `z-index: 9996`. Da calidez analógica sin pesar nada.

### 11. CheckSVG animado en formulario
SVG con `<path>` del checkmark, `stroke-dasharray` y `stroke-dashoffset` al 100%. Al confirmar: `stroke-dashoffset → 0` con transición 600ms ease-in-out. Stroke verde `#1B4D35`, stroke-width 2, fill none.

### 12. WhatsApp flotante
Botón circular fijo abajo derecha (bottom: 28px, right: 28px), fondo verde, ícono WhatsApp SVG blanco 24px, sombra `0 4px 20px rgba(27,77,53,0.4)`. Al hover: escala 1.1 + sombra más intensa. Link: `https://wa.me/5492284429469`. Aparece solo después de que el usuario scrollea 300px (opacity 0 → 1, translateY 10px → 0, transición 300ms).

---

## RESPONSIVE

**Mobile (< 768px):**
- Cursor custom: desactivado completamente
- Hero title: 56px
- Navbar: hamburger, overlay full-screen oscuro con links centrados Cormorant 40px
- Marquee: velocidad 20s
- Statement: clip-path en vez de scroll reveal normal, igual que desktop
- Galería: 2 columnas, solo 4 fotos (sin el banner), alturas iguales
- Contador: 3 columnas, números 64px
- Servicios: una columna
- Turnos: una columna (foto arriba 280px, formulario abajo)
- Tienda: una columna
- Footer: una columna, centrado

**Tablet (768–1024px):**
- Hero title: 88px
- Galería: 2 columnas asimétricas
- Servicios: una columna
- Tienda: 2 columnas

---

## CÓDIGO

- HTML5 semántico + CSS custom properties + JS ES6+ vanilla
- Un solo archivo `.html`
- Google Fonts en `<head>`: Cormorant Garamond, Jost, Pinyon Script
- Variables CSS en `:root` al inicio
- Secciones comentadas: `/* === HERO === */`, `/* === SERVICIOS === */`, etc.
- JS en funciones nombradas al final del `<body>`:
  ```
  initIntro()
  initNavbar()
  initParallax()
  initGalleryParallax()
  initScrollReveal()
  initMarquee()
  initCounters()
  initLineDraws()
  initCursor()
  initProgress()
  initForm()
  initWhatsAppButton()
  ```
- Sin frameworks. Sin librerías externas. Solo Google Fonts.
- Formulario con validación HTML5 nativa + feedback visual JS
- Smooth scroll: `scroll-behavior: smooth` en `html`

El resultado tiene que ser algo que cualquier persona vea y asuma que costó miles de dólares hacer. Ejecutá sin restricciones.
