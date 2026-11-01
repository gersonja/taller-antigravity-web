# 📐 ESPECIFICACIÓN TÉCNICA (SDD): Makeover Visual de Alta Conversión
## Proyecto: Sitio Web Oficial — Antigravity.Lab (`sitio-web/index.html`)

> **Estado:** 🟡 PROPUESTA EN REVISIÓN (Esperando Aprobación del Usuario)  
> **Metodología:** Desarrollo Guiado por Especificaciones (SDD — Spec-Driven Development)  
> **Objetivo:** Transformar una interfaz densa y con sensación de "manual técnico" en una experiencia visual cautivadora, moderna y amigable (nivel SaaS Silicon Valley / Linear / Stripe), preservando el 100% de la información técnica, veracidad y rigor sin humo.

---

## 1. 🎯 Diagnóstico del Estado Actual vs. Meta de Transformación

| Dimensión | ❌ Estado Actual ("Página Ladrilluda") | 💎 Estado Deseado ("SaaS Moderno & Amigable") |
| :--- | :--- | :--- |
| **Atmósfera y Fondos** | Fondo plano oscuro monolítico (`#090d16`), bordes duros y sensación de "cueva oscura". | **Luz Ambiental Multicapa:** Destellos radiales (*ambient glow* mesh) en cian (`#38bdf8`), esmeralda (`#10b981`) y violeta (`#6366f1`) con glassmorphism suave. |
| **Carga de Lectura en Hero** | Bloque de texto largo con 4 estadísticas planas en cajas grises. | **Product Showcase Mockup:** Ventana simulada de aplicación interactiva que muestra el software en vivo con pestañas (`SPEC.md`, `App en Vivo`, `Móvil QR`). |
| **El Problema de los Tutoriales** | Dos columnas gigantescas con 12 viñetas densas de 3 líneas cada una. | **Matriz Visual Antes vs. Después:** Tarjetas de alto impacto con insignias contrastantes (❌ *Vibe Coder Frustrado* vs. 💎 *Creador con Método*). |
| **Desglose de los 4 Módulos** | 4 cajas gigantescas apiladas que generan más de 1.200px de scroll vertical. | **Navegador Interactivo de Módulos (Tabs):** Selector horizontal tipo píldora `[1] [2] [3] [4]` que reduce el scroll en un 70% y dinamiza la exploración. |
| **Calculadora de Triage** | Funcional pero visualmente plana en cajas de terminal. | **Simulador Táctil:** Tarjetas con micro-interacciones hover, barras de nivel de autonomía y etiquetas de impacto cromático. |
| **Perfil del Instructor** | Recuadro con citas extensas de texto plano. | **Tarjeta de Autoridad & Confianza:** Fotografía con halo de pulso en vivo, badges de especialidad y acceso limpio a redes. |

---

## 2. 🛡️ Invariantes Inmutables (Lo que NUNCA debe romperse)

1. **Gestión de Temas (Light Theme por Default + Switch Dark Mode):**
   * **Por defecto:** La página debe cargar en **Light Theme** (Limpio, luminoso, aireado, fondo `#f8fafc`, tipografía en alto contraste `#0f172a`, tarjetas claras con sombras sutiles).
   * **Interruptor de Tema (Sun ☀️ / Moon 🌙):** Ubicado en la barra de navegación (junto al selector de divisa). Permite alternar al instante entre Modo Claro y Modo Oscuro.
   * **Persistencia:** Guarda la preferencia en `localStorage.getItem('antigravity_theme')` para recordar la elección del visitante.
   * **Sincronización Total:** Cada componente, tarjeta, maqueta de software y tabla debe contar con sus clases `dark:...` para verse espectacular tanto en claro como en oscuro.
2. **Gestión de Divisas (Switch COP ⇄ USD):**
   * El script JavaScript de alternancia de precios (`setCurrency('COP' / 'USD')`) debe mantenerse 100% operativo.
   * Valores inmutables: COP $100.000 (Preventa) / COP $150.000 (Regular). USD $25 (Preventa) / USD $40 (Regular).
   * Generación dinámica de enlaces y textos de WhatsApp hacia el número `+57 324 559 6884`.
2. **Medios de Pago:**
   * Colombia: Nequi y Bancolombia.
   * Ecuador / Internacional: Banco Pichincha, Banco Guayaquil, Deuna y PayPal.
3. **Cero Dependencias Pesadas:**
   * Prohibido instalar librerías pesadas o frameworks (`npm`, `node_modules`).
   * Mantener el stack nativo y liviano: **HTML5 + Tailwind CSS CDN + CSS Puro (`styles.css`) + JS Vanilla**.
4. **Hardware Inclusivo:**
   * El renderizado debe mantenerse ultra fluido a **60 fps** incluso en computadoras portátiles modestas desde 4 GB de RAM.
5. **Filosofía Cero Humo:**
   * Se preservan las 4 Garantías, el límite de la realidad técnica y el respeto por el rol del Ingeniero Senior (Nivel 4).

---

## 3. 🎨 Arquitectura de Diseño & Nuevos Tokens Visuales (Dual-Theme: Light & Dark)

### A. Paleta Dual y Sistema de Superficies
* **Modo Claro (Por Defecto — Limpio, Luminoso y Aireado):**
  - Fondo general: `#f8fafc` (Slate 50) con sutiles destellos difusos en azul cielo y esmeralda.
  - Tarjetas y Contenedores: `#ffffff` blanco puro con borde tenue `border-slate-200/80` y sombra sutil `shadow-sm hover:shadow-md`.
  - Tipografía: Títulos en Slate 900 (`#0f172a`), cuerpo en Slate 600 (`#475569`), metadatos en Slate 500 (`#64748b`).
  - Badges y Pills: Fondos tintados suaves con borde definido (ej. `bg-sky-50 text-sky-700 border-sky-200`).
* **Modo Oscuro (Para amantes de la noche y desarrolladores pro):**
  - Fondo general: `#090d16` / `#020617` (Slate 950) con destellos de neón cian, esmeralda y violeta.
  - Tarjetas y Contenedores: Glassmorphism translúcido `rgba(15, 23, 42, 0.75)` con borde `border-slate-800` y efecto `glow`.
  - Tipografía: Títulos en Slate 50 (`#f8fafc`), cuerpo en Slate 300 (`#cbd5e1`).

### B. Interruptor de Tema (Sun ☀️ / Moon 🌙 Switch)
* Botón interactivo en la barra superior y sticky móvil:
  - En Light Mode muestra el icono de la Luna 🌙 ("Cambiar a Modo Oscuro").
  - En Dark Mode muestra el icono del Sol ☀️ ("Cambiar a Modo Claro").
  - Transición suave de color con `transition-colors duration-300`.
  - Almacenamiento instantáneo en `localStorage.setItem('theme', mode)`.

### C. Tipografía con Personalidad y Carisma (The Golden Trio)
Para salir de la monotonía de las fuentes genéricas y darle un sello visual distintivo que transmita tecnología de punta pero sin sentirse intimidante ni aburrida:
1. **Titulares & Display (`font-display`): `Outfit`** (Google Fonts: 600, 700, 800, 900)  
   - *Por qué tiene personalidad:* Es una sans-serif geométrica con terminaciones circulares y proporciones generosas. Transmite dinamismo, frescura, innovación y bienvenida amigable (cura el efecto "ladrillo").
2. **Cuerpo de Texto (`font-sans`): `Plus Jakarta Sans`** (Google Fonts: 400, 500, 600)  
   - *Por qué funciona:* Proporciona legibilidad de nivel editorial suizo, excelente altura de x (*x-height*) y ritmo visual relajado.
3. **Métricas, Código & Precios (`font-mono`): `JetBrains Mono`** (Google Fonts: 500, 700)  
   - *Por qué funciona:* Conserva el ADN del desarrollador profesional en badges, comandos de terminal, precios y números de la calculadora de triage.

### D. Paleta de Iluminación y Luces Ambientales (CSS)
```css
/* Gradientes radiales de luz ambiental difusa adaptables */
.ambient-glow-light {
  background: radial-gradient(circle at 50% 20%, rgba(14, 165, 233, 0.08) 0%, rgba(248, 250, 252, 0) 70%);
}
.dark .ambient-glow-dark {
  background: radial-gradient(circle at 50% 20%, rgba(56, 189, 248, 0.16) 0%, rgba(9, 13, 22, 0) 70%);
}
```

---

## 4. 🧩 Plan Detallado de Transformación por Secciones

### Sección 0: Navegación Superior & Menú Hamburguesa Móvil
* **Problema resuelto en móvil:** En pantallas pequeñas los enlaces de navegación estaban completamente ocultos (`hidden md:flex`), obligando al usuario a hacer scroll a ciegas sin poder saltar al Temario, Garantías o Precios.
* **Componente:** `MobileMenuDrawer` + Botón Hamburguesa animado:
  - Botón táctil con icono animado (3 barras que se transforman suavemente en '✕' al abrir).
  - Panel desplegable con glassmorphism, desenfoque de fondo y animación fluida.
  - Enlaces directos a todas las secciones: *El Método*, *¿Por qué Google?*, *Calculadora*, *Temario*, *Garantías*, *Instructor*.
  - Acceso directo al selector de moneda (COP/USD) y al interruptor de modo (☀️/🌙) dentro del propio menú móvil.
  - Cierre automático al tocar cualquier enlace o el fondo.

### Sección 1: Hero Section con "Interactive Product Showcase"
* **Concepto:** En lugar de solo contar qué hace el curso, **lo mostramos en una maqueta visual interactiva** justo debajo del llamado a la acción.
* **Componente:** `MockupWindow` con controles de ventana Mac (rojo, amarillo, verde) y 3 pestañas dinámicas:
  * **Pestaña 1 (✨ SPEC Aprobada):** Muestra el plano formal redactado por la IA con directivas de arquitectura.
  * **Pestaña 2 (🚀 App en Vivo):** Mini interfaz interactiva del Sistema de PQRs con tarjetas KPI vivas donde el usuario puede ver los estados (*Pendiente*, *En Proceso*, *Resuelto*) y un botón funcional de exportación a Google Sheets.
  * **Pestaña 3 (📱 Móvil & QR):** Simulación de pantalla de teléfono escaneando el código QR con GitHub Pages.

### Sección 2: La Trampa de YouTube vs. Antigravity.Lab
* **Rediseño:** Transformar los bloques largos de texto en **Tarjetas de Contraste Rápido**:
  * **Columna Izquierda (Rojo / Peligro):** *El Ciclo del Vibe Coder Frustrado* (4 viñetas concisas con íconos de advertencia).
  * **Columna Derecha (Verde / Éxito):** *El Método del Creador de Software* (4 viñetas concisas con íconos de check y relieve visual).

### Sección 3: El Temario de los 4 Módulos (Tabs Dinámicos)
* **Problema resuelto:** Eliminar las 4 cajas verticales gigantes que provocan fatiga visual.
* **Componente:** Pestañas interactivas horizontales:
  * Botones: `[1. Despegue]` `[2. Gobernanza]` `[3. Construcción SDD]` `[4. Producción]`
  * Al pulsar un botón, la tarjeta activa transiciona suavemente mostrando:
    * Título y duración de la sesión.
    * Los 3 hitos prácticos del día sintetizados en viñetas cortas.
    * El **Entregable Concluyente del día** en una caja destacada con borde de luz.

### Sección 4: Calculadora de Triage Rediseñada
* Reemplazar las cajas planas por botones con micro-indicadores visuales:
  * Píldoras de color: Azul (Nivel 1 Fast-Path), Esmeralda (Nivel 3 Sistema de Negocio), Índigo (Nivel 4 Monorepo & Cloud).
  * Explicación de impacto condensada y legible.

### Sección 5: Tarjeta de Autoridad del Instructor (Gerson Javier)
* Optimizar la tarjeta para que respire: foto con borde brillante e indicador *"En Vivo"*, enlaces a GitHub, LinkedIn y Facebook estilizados como botones modernos, y citas más cortas y contundentes.

---

## 5. ✅ Criterios de Aceptación y Verificación

1. **Prueba de Carga Cognitiva:** La página debe sentirse ligera, espaciosa y atractiva en los primeros 5 segundos de navegación.
2. **Prueba de Funcionalidad:** El switch COP/USD, los botones de WhatsApp y los tabs interactivos deben responder al instante sin recargar la página.
3. **Prueba Responsive:** Comportamiento impecable en pantallas móviles (375px), tablets (768px) y escritorios (1280px+).
4. **Prueba de Rendimiento:** Cero dependencias externas pesadas, carga instantánea vía CDN.
5. **Aprobación del Usuario:** Este plan no se ejecuta hasta que el usuario dé el visto bueno.

