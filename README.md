# Componente TableOfContents para Astro

Un componente reutilizable de Tabla de Contenido (TOC) para proyectos Astro, con seguimiento de progreso y navegación suave.

## Instalación

```bash
npm install @olliebyte/astro-toc@1.0.5
# o
pnpm add @olliebyte/astro-toc@1.0.5
# o
yarn add @olliebyte/astro-toc@1.0.5
```

## Uso Básico

### Con headings manuales
```astro
---
import TableOfContents from '@olliebyte/astro-toc';

const headings = [
  { depth: 2, slug: 'introduccion', text: 'Introducción' },
  { depth: 3, slug: 'instalacion', text: 'Instalación' },
  { depth: 2, slug: 'uso', text: 'Uso' }
];
---

<TableOfContents headings={headings} />
```

### Detección automática (requiere headings con id en el mismo archivo)
```astro
---
import TableOfContents from '@olliebyte/astro-toc';
---

<!-- Los headings deben tener id para ser detectados -->
<h2 id="introduccion">Introducción</h2>
<h3 id="instalacion">Instalación</h3>
<h2 id="uso">Uso</h2>

<TableOfContents />
```

### Compatibilidad con SSR
El componente es totalmente compatible con Server-Side Rendering (SSR) en Astro. La detección automática de headings ocurre únicamente en el cliente, evitando errores relacionados con APIs del navegador en el servidor. La lógica del cliente se carga automáticamente solo en el navegador gracias al uso de `client:load`.

## Props

| Prop | Tipo | Requerido | Default | Descripción |
|------|------|-----------|---------|-------------|
| `headings` | `Array<{depth: number, slug: string, text: string}>` | Sí | - | Array de encabezados del documento |
| `title` | `string` | No | "Tabla de Contenido" | Título del componente |
| `showProgress` | `boolean` | No | `true` | Mostrar barra de progreso de lectura |
| `sticky` | `boolean` | No | `true` | Fijar el componente en la pantalla al hacer scroll |

## Personalización

Puedes personalizar los estilos usando las siguientes clases CSS:

```css
.toc-nav {
  /* Estilos para el contenedor de navegación */
}

.toc-link {
  /* Estilos para los enlaces */
}

.toc-link.active {
  /* Estilos para el enlace activo */
}

.progress-bar {
  /* Estilos para la barra de progreso */
}
```

## Características

- Seguimiento de progreso de lectura con optimización de rendimiento
- Navegación suave entre secciones
- Soporte para temas claro/oscuro
- Validación de props con Zod
- Accesibilidad mejorada (ARIA)
- Compatible con SSR (Server-Side Rendering)
- Compatible con Astro 5.0.0 y superiores

## Mejoras de Accesibilidad

El componente incluye las siguientes mejoras de accesibilidad:

- Atributos ARIA para mejorar la experiencia con lectores de pantalla
- Etiquetas descriptivas para cada enlace de navegación
- Elementos decorativos marcados como `aria-hidden="true"`
- Roles semánticos explícitos para mejor compatibilidad

## Optimizaciones de Rendimiento

- Throttling en la función de actualización de progreso para reducir cálculos
- Manejo eficiente de eventos de scroll
- Detección inteligente de encabezados visibles

## Ejemplo Completo

```astro
---
import TableOfContents from '@olliebyte/astro-toc';

const headings = [
  { depth: 2, slug: 'introduccion', text: 'Introducción' },
  { depth: 3, slug: 'instalacion', text: 'Instalación' },
  { depth: 2, slug: 'uso', text: 'Uso' },
];
---

<TableOfContents 
  headings={headings}
  title="Índice"
  showProgress={true}
  sticky={false}
/>
```

## Contribución

¡Las contribuciones son bienvenidas! Por favor, abre un issue o envía un PR.

## Licencia

MIT

<TableOfContents 
  headings={headings}
  title="Índice"
  showProgress={true}
  sticky={false}
/>
```

## Contribución

¡Las contribuciones son bienvenidas! Por favor, abre un issue o envía un PR.

## Licencia

MIT