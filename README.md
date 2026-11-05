# Portfolio Profesional — Valentín Gemetro

Documentación técnica y funcional del archivo [`index.html`](./index.html), desarrollado como una **Single Page Application (SPA)** de alto rendimiento, diseño bilingüe (Español / Inglés) y estética moderna basada en **Glassmorphism**, paleta **Obsidian / Violeta** y **Tailwind CSS**.

---

## 📌 Tabla de Contenidos
1. [Visión General del Proyecto](#-visión-general-del-proyecto)
2. [Estructura y Secciones de index.html](#-estructura-y-secciones-de-indexhtml)
3. [Sistema de Internacionalización (i18n)](#-sistema-de-internacionalización-i18n)
4. [Tecnologías, Librerías y APIs](#-tecnologías-librerías-y-apis)
5. [Catálogo de Íconos y Elementos Visuales](#-catálogo-de-íconos-y-elementos-visuales)
6. [Mapeo de URLs y Enlaces](#-mapeo-de-urls-y-enlaces)
7. [Scripts e Interactividad JavaScript](#-scripts-e-interactividad-javascript)
8. [Guía de Mantenimiento y Extensión](#-guía-de-mantenimiento-y-extensión)
9. [Instrucciones de Despliegue](#-instrucciones-de-despliegue)

---

## 🚀 Visión General del Proyecto

El sitio web representa el portafolio profesional de **Valentín Gemetro**, estudiante avanzado de Ingeniería en Sistemas de Información (Universidad Nacional del Sur, 5º año) y Desarrollador Full Stack.

El proyecto está diseñado bajo los siguientes pilares:
- **Cero dependencias pesadas de empaquetado:** Funciona directamente desde el navegador sin necesidad de compiladores como Webpack o Vite.
- **Renderizado fluido y ultrarrápido:** Estilos procesados en tiempo real mediante Tailwind CDN y fuentes tipográficas optimizadas con Google Fonts.
- **Soporte bilingüe transparente (ES/EN):** Cambio de idioma dinámico sin recargar la página, con almacenamiento persistente de preferencia en `localStorage`.
- **Identidad visual consistente:** Tema oscuro futurista (*Obsidian*) con tonos violetas luminosos, paneles translúcidos con efecto de desenfoque (*backdrop blur*) y cursor interactivo personalizado.

---

## 📐 Estructura y Secciones de `index.html`

El documento se divide de manera modular y semántica en las siguientes partes:

```
index.html
├── <head>
│   ├── Metadatos & Configuración del Viewport
│   ├── Google Fonts (Geist, Geist Mono, Inter, JetBrains Mono)
│   ├── Tailwind CSS v3 CDN + Configuración personalizada
│   └── Estilos Custom (Cursor, Ripple, Glass Panels, Orbes de luz)
├── <body>
│   ├── Componentes Globales (Cursor interactivo & Orbes ambientales)
│   ├── <header> (Navegación fija, Logo, Conmutador ES|EN, Botón de contacto)
│   ├── <main>
│   │   ├── #hero (Titular principal, resumen, CTAs, avatar y badges métricos)
│   │   ├── #about (Ficha personal, redes, bio ampliada, stack y destacados)
│   │   ├── #experience (Línea de tiempo: Neufitech, UNS docencia, carrera y certificaciones)
│   │   ├── #services (3 tarjetas de áreas técnicas y banner de 4 métricas)
│   │   ├── #projects (3 maquetas interactivas: Tienda River, Predictor Mundial, Previa App)
│   │   ├── #process (Metodología en 3 etapas: Definir, Desarrollar, Desplegar)
│   │   ├── #faqs (Acordeón interactivo con preguntas y respuestas)
│   │   └── #contact (Caja de conversión con email, LinkedIn, GitHub y teléfono)
│   ├── <footer> (Copyright, accesos rápidos y mención técnica)
│   └── <script> (Animación del cursor, Toggle del acordeón, Motor i18n)
```

### Detalle de cada Sección:

| Sección | ID Ancla | Propósito y Contenido |
| :--- | :--- | :--- |
| **Cabecera** | `header` | Barra flotante superior `glass-panel` que incluye el logo, anclas de navegación rápida, el selector bilingüe minimalista y el botón CTA. |
| **Hero** | `#hero` | Presentación de impacto: badge animado de estado (*Available for new challenges*), título con tipografía *Geist*, subtítulo del rol y 4 tarjetas orbitales con métricas reales (5º Año UNS, Full Stack, 3+ Proyectos, UNS & Neufitech). |
| **Sobre Mí** | `#about` | Perfil del desarrollador: tarjeta izquierda con avatar, estado de disponibilidad, enlaces a redes sociales y botón de contacto. Columna derecha con bio completa, chips de tecnologías principales y resumen rápido de experiencia. |
| **Trayectoria** | `#experience` | Timeline vertical con línea violeta luminosa y nodos de estado que detalla Neufitech (ecosistema SAI), Ayudantía en Bases de Datos (UNS), Ingeniería en Sistemas (UNS 5º año) y Certificaciones (IBM SkillsBuild, CACIC, UNESCO). |
| **Servicios** | `#services` | Grilla de 3 tarjetas técnicas (Desarrollo Web Full Stack, APIs & Backend Services, PWAs & Real-Time) con banner inferior de métricas de trayectoria. |
| **Proyectos** | `#projects` | 展示 (Showcase) de 3 aplicaciones en producción utilizando maquetas con barra de navegación simulada, credenciales demo, status de infraestructura, etiquetas de stack y botones directos hacia las demos en Vercel. |
| **Proceso** | `#process` | Metodología de desarrollo explicada en 3 fases numeradas con marcas de agua translúcidas (01: Definir & Arquitectar, 02: Construir & Desarrollar, 03: Desplegar & Optimizar). |
| **Preguntas Frecuentes** | `#faqs` | Acordeón responsivo que aclara especialidades, disponibilidad laboral, proyectos insignia, stack tecnológico y canales de contacto. |
| **Contacto** | `#contact` | Módulo de conversión con iluminación violeta envolvente, botones directos para enviar email, abrir LinkedIn y GitHub, además de teléfono directo y ubicación geográfica. |
| **Pie de Página** | `footer` | Cierre con copyright 2026, enlaces de navegación y distintivo de diseño. |

---

## 🌐 Sistema de Internacionalización (i18n)

El soporte bilingüe está implementado mediante un motor nativo en JavaScript ubicado al pie del documento, sin dependencias externas.

### 1. Marcado en el HTML: Atributos `data-i18n`
Cada elemento traducible en el HTML cuenta con el atributo `data-i18n="clave"`. Si el elemento contiene etiquetas HTML internas (como `<span>` con gradientes de color o saltos `<br>`), se añade además `data-i18n-html="true"`.

Ejemplos:
```html
<!-- Texto simple -->
<h2 data-i18n="about.title">Sobre Mí</h2>

<!-- Texto con HTML interno y estilos -->
<h1 data-i18n="hero.title" data-i18n-html="true">
  ¡Hola! Soy Valentín Gemetro, <br class="hidden sm:block"/>construyendo 
  <span class="italic font-display font-light text-transparent bg-clip-text bg-gradient-to-r from-brand-300 via-brand-400 to-purple-200 block sm:inline mt-1 sm:mt-0">
    Experiencias Digitales.
  </span>
</h1>
```

### 2. Diccionario de Traducción (`translations`)
Almacena un árbol de claves con réplicas idénticas para `es` (Español) y `en` (Inglés). Cuenta con **122 claves sincronizadas** que garantizan paridad 1:1.

```javascript
const translations = {
  es: {
    "page.title": "Valentín Gemetro — Desarrollador Full Stack & Estudiante de Ingeniería en Sistemas",
    "nav.projects": "Proyectos",
    "about.title": "Sobre Mí",
    // ...
  },
  en: {
    "page.title": "Valentín Gemetro — Full Stack Developer & Systems Engineering Student",
    "nav.projects": "Projects",
    "about.title": "About Me",
    // ...
  }
};
```

### 3. Función `setLanguage(lang)`
Se encarga de:
1. Validar el idioma solicitado (`es` o `en`, fallback a `es`).
2. Guardar la elección en el almacenamiento del navegador: `localStorage.setItem('portfolio_lang', lang)`.
3. Actualizar el atributo de idioma de la página: `document.documentElement.lang = lang`.
4. Actualizar el título de la pestaña del navegador (`document.title`).
5. Alternar la clase activa (`text-brand-300 font-bold`) en el botón del conmutador (`#lang-btn-es` y `#lang-btn-en`).
6. Recorrer todos los nodos con `document.querySelectorAll('[data-i18n]')` y sustituir su contenido (`textContent` o `innerHTML`).

### 4. Control de Idioma en la Barra de Navegación
Ubicado en el `<header>`:
```html
<button id="lang-toggle" type="button" aria-label="Cambiar idioma / Switch language" class="glass-badge px-3 py-1.5 rounded-full text-xs font-mono font-semibold tracking-wider hover:border-brand-400/50 transition-all duration-200 flex items-center gap-1.5 cursor-pointer">
  <span id="lang-btn-es" class="text-brand-300 font-bold transition-colors">ES</span>
  <span class="text-purple-400/40">|</span>
  <span id="lang-btn-en" class="text-purple-400/60 transition-colors">EN</span>
</button>
```
Al hacer clic, el event listener conmuta de `es` a `en` y viceversa en una sola acción interactiva.

---

## 🛠 Tecnologías, Librerías y APIs

### En la Interfaz Web (Frontend Portfolio)
- **HTML5:** Marcado semántico (`<header>`, `<main>`, `<section>`, `<article>`, `<footer>`).
- **Tailwind CSS v3 (CDN):** Framework utilitario cargado con plugins oficiales:
  - `container-queries` (adaptabilidad de componentes modulares).
  - `forms` (estandarización de elementos de formulario/interactivos).
- **Google Fonts:**
  - `Geist` & `Geist Mono`: Tipografía de precisión creada para interfaces de ingeniería de software.
  - `Inter`: Fuente base para legibilidad del cuerpo del texto.
  - `JetBrains Mono`: Tipografía para fragmentos técnicos, badges y chips de código.
- **Glassmorphism CSS:** Propiedades `backdrop-filter: blur(16px)` combinadas con bordes semitransparentes `rgba(168, 85, 247, 0.2)` para lograr paneles translúcidos.

### En los Proyectos Integrados del Desarrollador
| Proyecto | Tecnologías & APIs Clave |
| :--- | :--- |
| **Tienda River** | **Next.js**, **Node.js**, **PostgreSQL**, **Mercado Pago API (Checkout Pro)**, **Tailwind CSS**, **NextAuth**. |
| **Predictor Mundial** | **Next.js 14**, **FastAPI (Python 3)**, **Pydantic**, **Chakra UI**, **Framer Motion**, **TypeScript**. |
| **Previa App** | **Next.js 16**, **React 19**, **Firebase Realtime Database API**, **PWA (Progressive Web App)** con soporte Offline y emparejamiento QR. |

---

## 🎨 Catálogo de Íconos y Elementos Visuales

Todos los íconos del portafolio son **vectores SVG puros inline**, lo que garantiza:
- Cero peticiones de red adicionales por iconos.
- Cero desalineaciones por fuentes de iconos externas.
- Control total del color mediante clases Tailwind (`fill-current`, `stroke-current`, `text-brand-300`, etc.).

### Listado de Íconos Utilizados:
1. **Redes Sociales & Comunicación:**
   - **LinkedIn:** Logo oficial vectorial de LinkedIn en la tarjeta *Sobre Mí* y en la sección *Contacto*.
   - **GitHub:** Silueta del Octocat de GitHub con enlace al repositorio del desarrollador.
   - **Correo Electrónico (Email):** Ícono vectorial de sobre cerrado (`stroke-width="1.8"`).
   - **Teléfono / Llamada:** Ícono vectorial de auricular telefónico (`tel:+54...`).
2. **Tecnologías en el Tech Stack:**
   - **React / Next.js:** Símbolo atómico con órbitas elípticas animadas con rotación continua CSS (`animate-[spin_10s_linear_infinite]`).
   - **TypeScript / JavaScript:** Chip tipo moneda monoespaciado (`TS`).
   - **Python / FastAPI:** Chip estilizado en violeta neón (`PY`).
   - **PostgreSQL / Bases de Datos:** Chip verde esmeralda con tipografía monoespaciada (`SQL`).
3. **Servicios Técnicos:**
   - **Ventana de Código:** Terminal con controles semáforo superiores y llaves de código angulares (`< / >`).
   - **Multi-dispositivo (Responsive):** Monitor y smartphone sincronizados para simbolizar arquitecturas cross-platform y backend.
   - **Diseño & UI/UX:** Monitor con puntero de ratón y selector vectorial.
4. **Acordeón FAQs:**
   - Indicador de estado animado que alterna entre `✕` (cuando la respuesta está desplegada) y `+` (cuando está plegada).

---

## 🔗 Mapeo de URLs y Enlaces

### 1. Enlaces de Navegación Interna (Smooth Scrolling)
Todos los vínculos internos utilizan identificadores de anclaje acompañados por la clase `scroll-smooth` en la etiqueta `<html>`:
- `#hero`: Retorno a la presentación principal.
- `#about`: Sección biográfica y perfil.
- `#experience`: Línea temporal de trayectoria académica y laboral.
- `#services`: Áreas de servicio técnico y capacidades.
- `#projects`: Galería de proyectos destacados.
- `#process`: Metodología de trabajo.
- `#faqs`: Sección de preguntas frecuentes.
- `#contact`: Bloque de llamado a la acción final y contacto directo.

### 2. Enlaces Externos con Seguridad
Todos los enlaces externos que navegan hacia otros sitios incluyen los atributos de seguridad `target="_blank"` y `rel="noopener noreferrer"` para proteger contra vulnerabilidades de *tabnabbing*:

| Destino | URL Exacta |
| :--- | :--- |
| **LinkedIn** | `https://www.linkedin.com/in/valentin-gemetro-59808a332` |
| **GitHub** | `https://github.com/ValenSecundaria` |
| **Demo: Tienda River** | `https://proyecto-2-gemetro-didier-c6ni.vercel.app/` |
| **Demo: Predictor Mundial** | `https://predictor-de-mundiales-plataforma-f.vercel.app/` |
| **Demo: Previa App** | `https://junta-amigos-app.vercel.app/` |

### 3. Protocolos URI Nativo
- **Email directo:** `mailto:gemetrov@gmail.com` (abre el cliente de correo predeterminado del usuario).
- **Llamada telefónica:** `tel:+542932404925` (habilita la marcación directa en dispositivos móviles o aplicaciones de VoIP).

---

## ⚙️ Scripts e Interactividad JavaScript

El archivo contiene 4 bloques de script funcionales:

### 1. Configuración de Tailwind (`data-purpose="tailwind-config"`)
Define la extensión de colores (`brand` violetas, `obsidian` fondos oscuros) y sombras personalizadas (`violet-glow`, `violet-btn`, `violet-card`).

### 2. Cursor Interactivo & Efecto Onda (`data-purpose="custom-cursor-and-click-animations"`)
- Crea un punto central (`#cursor-dot`) y un anillo con inercia elástica (`#cursor-ring`) que sigue las coordenadas `clientX` y `clientY` del ratón vía `requestAnimationFrame`.
- Al pasar sobre enlaces (`<a>`), botones (`<button>`) o entradas, el anillo se expande (`cursor-hover`).
- Al hacer clic en cualquier lugar, genera dinámicamente un elemento temporal con la clase `.click-ripple` que reproduce una onda expansiva en violeta translúcido antes de destruirse tras 550ms.
- Respeta la preferencia de accesibilidad del sistema operativo (`prefers-reduced-motion`).

### 3. Lógica del Acordeón FAQs (`data-purpose="faq-accordion-toggle"`)
- Función `toggleFaq(button)` que alterna la clase `hidden` en el contenedor `.faq-content` y actualiza el glifo del icono entre `✕` y `+`, gestionando además el borde brillante `border-brand-500/40`.

### 4. Motor i18n (`data-purpose="i18n-engine"`)
- Gestiona el diccionario bilingüe, los observadores de cambio de idioma, el refresco del DOM y la persistencia en `localStorage`.

---

## 🔧 Guía de Mantenimiento y Extensión

### ¿Cómo agregar un nuevo proyecto?
1. Duplica uno de los bloques `<article class="glass-panel ...">` dentro del contenedor `#projects > .grid`.
2. Actualiza los enlaces de la maqueta superior y del botón inferior con la nueva URL de Vercel / GitHub.
3. Asigna atributos `data-i18n` a los textos del nuevo proyecto (por ejemplo `p4.title`, `p4.desc`).
4. Añade las claves correspondientes en los objetos `es` y `en` dentro del script `i18n-engine`.

### ¿Cómo añadir o modificar un texto traducible?
1. Agrega el atributo `data-i18n="mi_seccion.mi_clave"` en el elemento HTML deseado.
2. Abre la sección `<script data-purpose="i18n-engine">` al final de `index.html`.
3. Introduce la clave `"mi_seccion.mi_clave"` tanto en el bloque `es` como en el bloque `en`.

---

## 🚢 Instrucciones de Despliegue

Dado que el portafolio consta de un único archivo estático (`index.html`), su despliegue es inmediato en cualquier plataforma:

### Opción 1: Vercel
1. Conecta el repositorio de GitHub en [vercel.com](https://vercel.com).
2. Deja los ajustes de *Build Command* y *Output Directory* vacíos (proyecto estático).
3. Haz clic en **Deploy**.

### Opción 2: GitHub Pages
1. Ve a **Settings > Pages** en el repositorio de GitHub.
2. En **Branch**, selecciona `main` y directorio `/ (root)`.
3. Guarda los cambios. Tu sitio estará disponible en `https://valensecundaria.github.io/portfolio/`.

### Opción 3: Netlify / Cloudflare Pages
1. Arrastra la carpeta del proyecto a la consola de Netlify Drop o vincula el repositorio en Cloudflare Pages para despliegues continuos automáticos.

---

*Documentación generada para Valentín Gemetro — 2026.*
