# SPEC-001 — Sitio institucional responsive

- **Estado:** Lista para implementación inicial
- **Versión:** 1.0.0
- **Fecha:** 2026-07-17
- **Producto:** Página ACA
- **Fase:** 1 — Sitio institucional
- **Especificación superior:** `SPEC-000-master.md`

## 1. Objetivo

Entregar la primera versión pública de Página ACA para la Asociación Civil Cetreros Argentinos, con navegación clara, identidad visual coherente y adaptación completa a móvil, tablet y escritorio.

Esta versión debe:

- Presentar a ACA y su actividad institucional.
- Brindar una introducción responsable a la cetrería.
- Centralizar actividades, novedades, galería, información para asociarse y contacto.
- Preparar una base técnica reutilizable para las futuras áreas privada y administrativa.
- Evitar publicar como definitivos datos que todavía no hayan sido validados por ACA.

## 2. Resultado esperado

Al finalizar esta especificación existirá una aplicación Next.js pública, responsive y accesible que:

- Puede desplegarse sin base de datos.
- Obtiene el contenido institucional desde archivos de configuración tipados.
- Utiliza el logo aportado por ACA.
- Permite reemplazar textos, enlaces, imágenes y datos de contacto sin modificar componentes.
- Mantiene visible el futuro acceso de socios sin implementar autenticación.
- Supera lint, verificación de tipos, pruebas y build de producción.

## 3. Alcance

### 3.1 Incluido

- Inicialización del proyecto Next.js con App Router y TypeScript estricto.
- Layout público común.
- Header responsive.
- Navegación móvil accesible.
- Footer institucional.
- Página de inicio.
- Página de la asociación.
- Página introductoria sobre cetrería.
- Página de actividades.
- Página de noticias o novedades.
- Página de galería.
- Página para asociarse.
- Página de contacto.
- Página de privacidad.
- Página informativa de acceso de socios en desarrollo.
- Página `404`.
- Metadatos SEO básicos.
- `sitemap.xml` y `robots.txt`.
- Componentes reutilizables.
- Contenido provisional claramente identificado en código y documentación.
- Pruebas básicas de rutas, navegación y comportamiento responsive.
- Configuración inicial de GitHub Actions.

### 3.2 No incluido

- Autenticación.
- Base de datos.
- Alta o edición de socios.
- Panel administrativo.
- Carnet virtual.
- Pagos o cuotas.
- Inscripción online a eventos.
- Gestión de contenido desde un CMS.
- Envío de formularios a servicios externos.
- Publicación automática de la comisión directiva.
- Analítica, publicidad o cookies no esenciales.
- Aplicación móvil nativa.

## 4. Usuarios y necesidades

### 4.1 Visitante general

Necesita comprender qué es ACA, qué actividades realiza y cómo contactarse.

### 4.2 Persona interesada en la cetrería

Necesita una introducción clara, prudente y no sensacionalista, con acceso a material aprobado por ACA.

### 4.3 Persona interesada en asociarse

Necesita conocer el proceso, requisitos y canal oficial de consulta, una vez que ACA proporcione esa información.

### 4.4 Socio actual

Necesita encontrar información institucional y reconocer que el acceso privado será incorporado en una fase posterior.

### 4.5 Responsable institucional

Necesita poder actualizar datos centralizados sin buscar textos repetidos en múltiples componentes.

## 5. Fuentes y contenido autorizado

### 5.1 Regla general

No se inventarán:

- Autoridades o cargos.
- Cantidad de socios.
- Domicilios, teléfonos, correos o redes sociales.
- Fechas de eventos.
- Beneficios o requisitos para asociarse.
- Declaraciones legales.
- Cifras o logros institucionales.

Los valores todavía no confirmados deben mantenerse en configuración como `null`, deshabilitados o identificados como provisionales.

### 5.2 Logo

Se utilizará el logo provisto por el responsable del proyecto.

Ruta objetivo:

```text
public/images/brand/logo-aca.jpg
```

Requisitos:

- No deformarlo.
- Mantener su proporción.
- No aplicar filtros que alteren sus colores.
- Mostrarlo con tamaño legible sin dominar innecesariamente la interfaz.
- Incluir alternativa textual: `Logo de la Asociación Cetreros Argentinos`.
- Preparar el componente para reemplazarlo por una versión vectorial o de mayor calidad en el futuro.

### 5.3 Fotografías

Solo podrán publicarse imágenes:

- Entregadas o aprobadas por ACA.
- Con permiso de publicación.
- Que no expongan datos personales innecesarios.
- Que no presenten prácticas riesgosas fuera de contexto.
- Que tengan texto alternativo adecuado.

Hasta recibir fotografías aprobadas se usarán bloques visuales neutros, ilustraciones propias autorizadas o espacios reservados. No se descargarán imágenes de terceros sin licencia comprobada.

## 6. Identidad visual provisional

La identidad se deriva del logo disponible y deberá ser validada por ACA antes de considerarse oficial.

### 6.1 Paleta

```text
--color-brand-sky:       #6FA0D0
--color-brand-sky-dark:  #345F8A
--color-brand-yellow:    #FFC400
--color-brand-black:     #111111
--color-brand-white:     #FFFFFF
--color-surface:         #F6F8FA
--color-border:          #D8DEE4
--color-text:            #1B1F23
--color-text-muted:      #59636E
--color-danger:          #B42318
--color-success:         #18794E
```

Reglas:

- El amarillo será un acento y no se utilizará como color principal para textos largos.
- Los textos deben mantener contraste WCAG AA.
- Para botones principales se priorizará `brand-sky-dark` con texto blanco.
- El negro se utilizará en texto y detalles, no como fondo dominante de todas las páginas.
- Ninguna información se comunicará únicamente mediante color.

### 6.2 Tipografía

Tipografía provisional:

- Interfaz: `Geist Sans`, cargada mediante `next/font`.
- Alternativas: `Arial`, `Helvetica`, `sans-serif`.
- No se dependerá de una fuente remota cargada en tiempo de ejecución.

Escala orientativa:

```text
Display:  clamp(2.25rem, 5vw, 4.75rem)
H1:       clamp(2rem, 4vw, 3.5rem)
H2:       clamp(1.6rem, 3vw, 2.5rem)
H3:       clamp(1.25rem, 2vw, 1.75rem)
Body:     1rem
Small:    0.875rem
```

### 6.3 Estilo

- Institucional, sobrio y cercano.
- Uso amplio de espacio en blanco.
- Bordes suaves y sombras discretas.
- Fotografías amplias cuando exista material aprobado.
- Evitar una estética militar, agresiva o de comercio de fauna.
- Evitar animaciones decorativas excesivas.
- El diseño debe transmitir asociación, formación, comunidad y responsabilidad.

## 7. Arquitectura de información y rutas

| Ruta | Nombre visible | Propósito |
|---|---|---|
| `/` | Inicio | Resumen y accesos principales |
| `/asociacion` | La asociación | Historia, misión, objetivos y comisión validada |
| `/cetreria` | Cetrería | Introducción educativa |
| `/actividades` | Actividades | Encuentros, jornadas y eventos |
| `/noticias` | Noticias | Novedades institucionales |
| `/galeria` | Galería | Imágenes aprobadas |
| `/asociarse` | Asociarse | Proceso y canal de consulta |
| `/contacto` | Contacto | Datos institucionales confirmados |
| `/privacidad` | Privacidad | Tratamiento de datos del sitio público |
| `/acceso-socios` | Acceso de socios | Página informativa de funcionalidad futura |

No habrá rutas dinámicas de noticias o actividades en el primer incremento, salvo que exista contenido suficiente y aprobado antes de la implementación.

## 8. Navegación

### 8.1 Header de escritorio

Orden:

1. Logo y nombre abreviado.
2. Inicio.
3. La asociación.
4. Cetrería.
5. Actividades.
6. Noticias.
7. Galería.
8. Asociarse.
9. Contacto.
10. Botón `Acceso de socios`.

Reglas:

- El logo enlaza a `/`.
- El enlace de la ruta actual utiliza `aria-current="page"`.
- El header puede permanecer fijo al desplazarse si no reduce demasiado el área útil.
- No habrá menús desplegables en la primera versión.
- El botón `Acceso de socios` dirige a `/acceso-socios`; no mostrará formulario de autenticación.

### 8.2 Navegación móvil

- Se muestra un botón con nombre accesible `Abrir menú`.
- Al abrirse, el nombre cambia a `Cerrar menú`.
- El panel contiene todos los enlaces en el mismo orden que escritorio.
- El foco pasa al primer enlace del panel.
- `Escape` cierra el menú.
- Al cerrar, el foco vuelve al botón activador.
- El scroll del documento queda bloqueado mientras el panel está abierto.
- Seleccionar un enlace cierra el panel.
- No debe existir desplazamiento horizontal.
- La interacción no depende de `hover`.

### 8.3 Skip link

La primera opción interactiva será `Saltar al contenido principal` y deberá hacerse visible al recibir foco.

## 9. Layout global

### 9.1 Estructura

```text
<body>
  SkipLink
  SiteHeader
  <main id="main-content">
    PageContent
  </main>
  SiteFooter
</body>
```

### 9.2 Contenedor

- Ancho máximo orientativo: `1200px`.
- Padding lateral mínimo: `16px`.
- En tablet: `24px`.
- En escritorio: `32px`.
- Las secciones de ancho completo pueden usar fondos diferentes, manteniendo el contenido dentro del contenedor.

### 9.3 Espaciado

Sistema basado en múltiplos de 4:

```text
4, 8, 12, 16, 24, 32, 48, 64, 96
```

## 10. Especificación por página

### 10.1 Inicio `/`

Orden obligatorio:

1. Hero.
2. Presentación breve de ACA.
3. Introducción a la cetrería.
4. Actividades destacadas.
5. Motivos para acercarse o asociarse.
6. Noticias recientes.
7. Llamado a la acción.
8. Contacto resumido.

#### Hero

Contenido:

- Etiqueta opcional: `Asociación Civil Cetreros Argentinos`.
- Título provisional: `Cetrería, formación y comunidad`.
- Texto provisional: presentación breve sin atribuir datos no confirmados.
- CTA principal: `Conocer la asociación`.
- CTA secundario: `Quiero asociarme`.
- Logo o fotografía aprobada.

Requisitos:

- Un único `h1`.
- CTA principal visible sin desplazamiento en pantallas comunes.
- El contenido debe seguir siendo legible sin imagen.
- No usar video automático.

#### Presentación de ACA

- Título.
- Texto institucional provisional.
- Enlace a `/asociacion`.
- No mostrar cifras de socios ni años de trayectoria sin validación.

#### Introducción a la cetrería

- Definición breve aprobable.
- Enfoque educativo y responsable.
- Enlace a `/cetreria`.
- No incluir instrucciones operativas sensibles o de captura, manejo o adquisición de fauna.

#### Actividades destacadas

- Hasta tres tarjetas.
- Si no hay actividades confirmadas, mostrar: `Próximamente publicaremos las actividades de ACA`.
- No inventar fechas.

#### Motivos para asociarse

Hasta tres bloques provisionales:

- Comunidad.
- Formación.
- Participación institucional.

Deben presentarse como orientación general hasta que ACA confirme beneficios formales.

#### Noticias recientes

- Hasta tres tarjetas.
- Sin contenido confirmado, mostrar estado vacío.
- No incluir fechas ficticias.

#### Llamado a la acción

- Título breve.
- Botón a `/asociarse`.
- Enlace secundario a `/contacto`.

### 10.2 La asociación `/asociacion`

Secciones:

1. Encabezado de página.
2. Quiénes somos.
3. Historia.
4. Misión, visión y objetivos.
5. Valores.
6. Comisión directiva.
7. CTA de contacto.

Reglas:

- Historia, misión, visión y objetivos deben provenir de configuración.
- La comisión solo se muestra cuando `board.isPublished === true`.
- Cada autoridad puede mostrar nombre, cargo y período únicamente si fue aprobado.
- No se publican DNI, domicilio, teléfono personal ni correo privado.
- Si la comisión no está aprobada, mostrar: `La información de la comisión directiva se encuentra en proceso de actualización`.

### 10.3 Cetrería `/cetreria`

Secciones:

1. Qué es la cetrería.
2. Historia y tradición.
3. Bienestar y responsabilidad.
4. Formación.
5. Marco normativo.
6. CTA a contacto.

Reglas:

- El contenido debe ser introductorio.
- No debe brindar instrucciones para capturar, adquirir o comercializar fauna.
- Las afirmaciones legales deben incluir fuente y fecha de revisión.
- Mientras no exista contenido legal validado, mostrar un aviso para consultar a las autoridades competentes.
- Evitar presentar a ACA como autoridad estatal.

### 10.4 Actividades `/actividades`

Contenido:

- Encabezado.
- Próximas actividades.
- Actividades anteriores, si existe material.
- Estado vacío.
- CTA de contacto.

Modelo mínimo:

```ts
type PublicActivity = {
  id: string;
  title: string;
  summary: string;
  startDate: string | null;
  endDate: string | null;
  location: string | null;
  image: PublicImage | null;
  status: "draft" | "published" | "cancelled";
};
```

Solo se renderizan actividades con estado `published`.

### 10.5 Noticias `/noticias`

Contenido:

- Encabezado.
- Lista de novedades.
- Estado vacío.
- Fecha de publicación cuando sea real.
- Enlaces externos identificados como tales.

Modelo mínimo:

```ts
type PublicNewsItem = {
  id: string;
  title: string;
  summary: string;
  publishedAt: string;
  image: PublicImage | null;
  externalUrl: string | null;
  status: "draft" | "published";
};
```

Solo se renderizan elementos `published`.

### 10.6 Galería `/galeria`

- Grilla responsive.
- Cada imagen incluye texto alternativo.
- No mostrar nombres de personas salvo autorización.
- Las imágenes no deben abrir automáticamente una nueva pestaña.
- Un visor ampliado es opcional; si se implementa debe ser accesible por teclado.
- Sin material aprobado, mostrar estado vacío.

### 10.7 Asociarse `/asociarse`

Secciones:

1. Introducción.
2. Requisitos.
3. Proceso.
4. Documentación solicitada.
5. Preguntas frecuentes.
6. CTA a contacto.

Reglas:

- No habrá formulario de alta en Fase 1.
- Todos los requisitos deben estar confirmados por ACA.
- Si están pendientes, mostrar una explicación y un canal oficial de consulta.
- No solicitar DNI, domicilio, certificados ni fotografías desde esta página.

### 10.8 Contacto `/contacto`

Puede mostrar únicamente datos confirmados:

- Correo institucional.
- Teléfono o WhatsApp institucional.
- Redes sociales oficiales.
- Domicilio institucional, si ACA autoriza su publicación.
- Horarios de atención, si existen.

Reglas:

- Los datos provienen de una configuración central.
- Los enlaces externos usan nombres comprensibles.
- Los enlaces a WhatsApp no incluyen datos personales precargados.
- No habrá formulario de contacto en el primer incremento.
- Si no existe un canal confirmado, mostrar: `Los canales oficiales de contacto se publicarán próximamente`.

### 10.9 Privacidad `/privacidad`

Debe explicar:

- Responsable del sitio, cuando esté confirmado.
- Qué datos procesa la web pública.
- Que en Fase 1 no se registran cuentas ni datos de socios.
- Uso técnico de logs del proveedor de hosting.
- Canal para consultas de privacidad.
- Fecha de última actualización.

No se utilizará una política genérica presentada como asesoramiento legal definitivo. El texto final deberá ser revisado por ACA.

### 10.10 Acceso de socios `/acceso-socios`

- Título: `Acceso de socios`.
- Mensaje: `El área privada de socios se encuentra en desarrollo`.
- Explicación breve de futuras funciones.
- Enlace a inicio y contacto.
- No mostrar campos de usuario o contraseña.
- La página debe usar `noindex` hasta que la funcionalidad esté disponible.

### 10.11 Página 404

- Mensaje claro.
- Enlace a inicio.
- Enlace a contacto.
- Mantener header y footer.

## 11. Componentes requeridos

```text
components/
├── brand/
│   └── BrandLogo
├── layout/
│   ├── SiteHeader
│   ├── MobileNavigation
│   ├── SiteFooter
│   ├── Container
│   ├── Section
│   └── SkipLink
├── ui/
│   ├── Button
│   ├── LinkButton
│   ├── Card
│   ├── Badge
│   ├── EmptyState
│   ├── PageHeader
│   └── ResponsiveImage
└── public-content/
    ├── ActivityCard
    ├── NewsCard
    ├── BoardMemberCard
    ├── ContactChannels
    └── GalleryGrid
```

Reglas:

- Los componentes de servidor serán la opción predeterminada.
- Solo usar `"use client"` para interacciones necesarias, como el menú móvil.
- No mezclar datos institucionales fijos dentro de componentes visuales.
- Los enlaces internos usarán `next/link`.
- Las imágenes usarán `next/image` cuando corresponda.

## 12. Configuración y contenido tipado

Estructura sugerida:

```text
src/
├── content/
│   ├── site.ts
│   ├── association.ts
│   ├── falconry.ts
│   ├── activities.ts
│   ├── news.ts
│   ├── gallery.ts
│   └── membership.ts
├── config/
│   ├── navigation.ts
│   └── seo.ts
└── types/
    └── public-content.ts
```

Ejemplo:

```ts
export const siteConfig = {
  legalName: "Asociación Civil Cetreros Argentinos",
  shortName: "ACA",
  description: "Sitio institucional de la Asociación Civil Cetreros Argentinos.",
  contact: {
    email: null,
    phone: null,
    whatsapp: null,
    address: null,
  },
  social: {
    instagram: null,
    facebook: null,
    youtube: null,
  },
} as const;
```

Los componentes deben ocultar de forma segura cualquier canal cuyo valor sea `null`.

## 13. Responsive design

Enfoque mobile-first.

### 13.1 Rangos de referencia

```text
Base:  0–639 px
sm:    640 px
md:    768 px
lg:    1024 px
xl:    1280 px
```

Los breakpoints no justifican diseños rígidos; deben usarse según el contenido.

### 13.2 Comportamiento esperado

#### 320–639 px

- Navegación móvil.
- Una columna.
- Botones principales de ancho completo cuando sea útil.
- Tarjetas apiladas.
- Tipografía fluida.
- Imágenes sin desbordamiento.
- Padding lateral mínimo de 16 px.

#### 640–1023 px

- Una o dos columnas según el contenido.
- Navegación móvil o de escritorio según espacio real.
- Tarjetas en grilla de dos columnas cuando sean legibles.

#### 1024 px o más

- Navegación de escritorio.
- Hero de dos columnas cuando exista imagen.
- Grillas de hasta tres columnas.
- Contenido limitado por ancho máximo.

### 13.3 Viewports obligatorios de prueba

- `320 × 568`.
- `375 × 667`.
- `768 × 1024`.
- `1024 × 768`.
- `1440 × 900`.

En ninguno debe existir scroll horizontal causado por el sitio.

## 14. Accesibilidad

Objetivo: WCAG 2.2 nivel AA en los flujos principales.

Requisitos:

- Navegación completa por teclado.
- Foco visible y orden lógico.
- `lang="es-AR"`.
- Un `h1` por página.
- Jerarquía de encabezados sin saltos arbitrarios.
- Texto alternativo útil.
- Iconos decorativos ocultos a tecnologías asistivas.
- Controles con nombre accesible.
- Áreas táctiles de aproximadamente 44 × 44 px.
- Respeto por `prefers-reduced-motion`.
- No reproducir audio o video automáticamente.
- Mensajes no dependientes únicamente de color.
- Enlaces distinguibles del texto normal.
- La ampliación de texto al 200 % no debe romper funciones esenciales.

## 15. SEO y metadatos

Cada ruta pública tendrá:

- `title`.
- `description`.
- URL canónica.
- Open Graph básico.
- Imagen social cuando exista un recurso aprobado.
- Metadatos consistentes mediante la API de Metadata de Next.js.

También se implementará:

- `sitemap.xml`.
- `robots.txt`.
- `metadataBase` configurado con `NEXT_PUBLIC_SITE_URL`.
- `noindex` para `/acceso-socios` mientras sea una página provisional.

Datos estructurados:

- Podrá utilizarse `Organization` únicamente con información confirmada.
- No se incluirán perfiles sociales, dirección o teléfono nulos o no verificados.

## 16. Rendimiento

Objetivos en páginas principales, evaluados en condiciones razonables:

- Lighthouse Performance: 90 o superior.
- Accessibility: 95 o superior.
- Best Practices: 95 o superior.
- SEO: 95 o superior.

Requisitos:

- Imágenes optimizadas.
- Evitar JavaScript de cliente innecesario.
- Sin librerías grandes para interacciones simples.
- Sin carruseles automáticos.
- Reservar dimensiones de imágenes para evitar saltos.
- Cargar contenido crítico primero.
- No utilizar video como fondo del hero.
- El logo no debe exceder el tamaño necesario.

## 17. Seguridad y privacidad

- No incluir secretos en variables `NEXT_PUBLIC_*`.
- No incluir datos reales de socios en repositorio, fixtures, pruebas o capturas.
- No utilizar HTML sin sanitizar.
- Enlaces externos con `rel="noopener noreferrer"` cuando abren otra pestaña.
- No incorporar scripts externos sin ADR y revisión.
- No incorporar analítica en la primera versión.
- No utilizar cookies no esenciales.
- No publicar metadatos EXIF innecesarios en imágenes.
- No presentar información provisional como oficial.

## 18. Estados de contenido

Todos los listados deben contemplar:

- Contenido disponible.
- Estado vacío.
- Elemento en borrador, que no se renderiza.
- Recurso visual ausente.
- Enlace externo ausente.
- Fecha ausente cuando el tipo lo permite.

No se usarán tarjetas ficticias para llenar el diseño.

## 19. Manejo de errores

- Los errores de renderizado no deben exponer detalles internos.
- Enlaces inválidos se detectarán en pruebas cuando sea posible.
- Las imágenes faltantes utilizarán una presentación neutra, no una URL rota visible.
- La página `404` debe conservar navegación.
- Durante build, datos de configuración inválidos deben fallar con un mensaje comprensible.

## 20. Validación de datos

Los archivos de contenido podrán validarse con Zod durante build.

Ejemplos de reglas:

- URL válida o `null`.
- Correo válido o `null`.
- Identificador único.
- Fecha ISO válida.
- Elementos `published` con título y resumen.
- Imágenes con `src`, `width`, `height` y `alt`.
- Autoridades publicadas con nombre, cargo y aprobación explícita.

## 21. Pruebas

### 21.1 Verificación estática

- ESLint.
- TypeScript con `strict: true`.
- Build de producción.
- Formateo consistente.

### 21.2 Unitarias

Cubrir como mínimo:

- Configuración de navegación.
- Filtrado de actividades publicadas.
- Filtrado de noticias publicadas.
- Ocultamiento de canales de contacto nulos.
- Validación de contenido.

### 21.3 Componentes

Cubrir como mínimo:

- Header.
- Menú móvil.
- Footer.
- Empty state.
- Tarjetas de actividad y noticias.

### 21.4 End-to-end

Escenarios mínimos:

1. El visitante puede navegar desde inicio a todas las rutas públicas.
2. El menú móvil abre, cierra y devuelve el foco.
3. `Escape` cierra el menú móvil.
4. La página actual está indicada.
5. No existen enlaces principales rotos.
6. `/acceso-socios` no presenta campos de autenticación.
7. El sitio no presenta scroll horizontal en viewports obligatorios.
8. La comisión no aparece si no está aprobada.
9. Los canales de contacto nulos no generan enlaces vacíos.

### 21.5 Accesibilidad automática

Ejecutar una herramienta como `axe-core` sobre:

- `/`.
- `/asociacion`.
- `/cetreria`.
- `/asociarse`.
- `/contacto`.

La ausencia de errores automáticos no reemplaza una revisión manual por teclado.

## 22. GitHub Actions

Crear:

```text
.github/workflows/ci.yml
```

Debe ejecutarse en `pull_request` y en pushes a `main`.

Pasos mínimos:

1. Checkout.
2. Configurar Node LTS.
3. Instalar dependencias con lockfile.
4. Ejecutar lint.
5. Ejecutar typecheck.
6. Ejecutar pruebas.
7. Ejecutar build.

Las pruebas end-to-end podrán ejecutarse en un job separado si aumentan demasiado el tiempo del job principal.

## 23. Estructura técnica inicial

```text
ACA/
├── AGENTS.md
├── CONTRIBUTING.md
├── README.md
├── docs/
├── public/
│   └── images/
│       └── brand/
│           └── logo-aca.jpg
├── src/
│   ├── app/
│   │   ├── page.tsx
│   │   ├── asociacion/page.tsx
│   │   ├── cetreria/page.tsx
│   │   ├── actividades/page.tsx
│   │   ├── noticias/page.tsx
│   │   ├── galeria/page.tsx
│   │   ├── asociarse/page.tsx
│   │   ├── contacto/page.tsx
│   │   ├── privacidad/page.tsx
│   │   ├── acceso-socios/page.tsx
│   │   ├── not-found.tsx
│   │   ├── layout.tsx
│   │   └── globals.css
│   ├── components/
│   ├── config/
│   ├── content/
│   ├── lib/
│   └── types/
└── tests/
```

## 24. Criterios de aceptación

La especificación se considera implementada cuando:

1. Todas las rutas definidas responden correctamente.
2. Existe un único layout público reutilizado.
3. El header funciona con teclado, mouse y táctil.
4. El menú móvil cumple apertura, cierre, foco y tecla `Escape`.
5. No existe scroll horizontal en los viewports obligatorios.
6. El contenido institucional se obtiene desde archivos tipados.
7. Los valores `null` no generan texto, iconos o enlaces vacíos.
8. El logo conserva proporción y tiene alternativa textual.
9. La comisión directiva no se publica sin aprobación explícita.
10. No hay datos reales de socios.
11. `/acceso-socios` es informativa y no implementa login.
12. Cada página posee título, descripción y un `h1`.
13. Existe `sitemap.xml` y `robots.txt`.
14. La navegación principal no contiene enlaces rotos.
15. Las imágenes están optimizadas y poseen dimensiones.
16. Se respetan foco visible, contraste y reducción de movimiento.
17. El sitio supera lint y typecheck.
18. Las pruebas unitarias y end-to-end mínimas pasan.
19. El build de producción termina correctamente.
20. GitHub Actions valida los pull requests.
21. README incluye comandos de instalación, desarrollo, pruebas y build.
22. Toda información pendiente sigue marcada como provisional.
23. No se incorporaron funciones fuera del alcance de esta fase.

## 25. Definition of Done del incremento

- Código revisable y dividido en componentes.
- Sin errores de TypeScript.
- Sin advertencias graves del navegador.
- Sin secretos o datos personales.
- Pruebas ejecutadas.
- Capturas de móvil y escritorio incorporadas al pull request.
- Documentación actualizada.
- Decisiones visuales provisionales identificadas.
- Aprobación manual del responsable del proyecto antes de fusionar a `main`.

## 26. Contenido pendiente de ACA

Los siguientes elementos no bloquean la construcción técnica, pero sí la publicación definitiva:

- Confirmación del logo y autorización de uso.
- Archivo del logo en mejor resolución o formato vectorial.
- Paleta oficial.
- Historia institucional.
- Misión, visión y objetivos.
- Comisión directiva vigente.
- Datos oficiales de contacto.
- Redes sociales oficiales.
- Requisitos para asociarse.
- Actividades y noticias iniciales.
- Fotografías autorizadas.
- Texto de privacidad revisado.
- Dominio definitivo.

## 27. Decisiones resueltas por esta especificación

- Se utilizará TypeScript estricto.
- Se utilizará Next.js App Router.
- La aplicación pública no requerirá base de datos.
- El contenido inicial estará centralizado en archivos tipados.
- La interfaz será mobile-first.
- El área de socios será solo informativa.
- No habrá formulario de contacto ni de asociación en Fase 1.
- No habrá analítica ni cookies no esenciales.
- El sistema visual será provisional y derivado del logo.
- Los datos no confirmados se ocultarán o se mostrarán como pendientes, nunca como definitivos.

## 28. Preguntas no bloqueantes para la publicación final

- ¿El nombre público preferido será `Asociación Cetreros Argentinos`, `Asociación Civil Cetreros Argentinos` o `ACA`?
- ¿El logo aportado es la versión oficial vigente?
- ¿Existe una versión SVG o PNG con transparencia?
- ¿Qué dominio se utilizará?
- ¿Qué textos institucionales serán aprobados?
- ¿Qué canales de contacto y redes se publicarán?
- ¿Qué información de la comisión está autorizada?
- ¿Se desea mostrar contenido normativo con enlaces externos oficiales?
