# SPEC-000 — Especificación maestra de Página ACA

- **Estado:** Borrador inicial
- **Versión:** 0.1.0
- **Fecha:** 2026-07-17
- **Producto:** Página ACA
- **Entidad:** Asociación Civil Cetreros Argentinos

## 1. Objetivo

Construir una plataforma web responsive para la Asociación Civil Cetreros Argentinos que comience como sitio institucional y evolucione hacia un sistema seguro de gestión de socios, comisión directiva, usuarios administrativos y carnets virtuales verificables.

## 2. Contexto confirmado

La entidad figura públicamente registrada como **Asociación Civil Cetreros Argentinos**, con constitución informada el 26 de junio de 2017 en la provincia de Santa Fe. La composición actual de la comisión directiva deberá ser proporcionada y validada por la asociación antes de publicarse.

## 3. Alcance por fases

### Fase 1 — Sitio institucional responsive

Incluye:

- Inicio.
- Quiénes somos.
- Introducción a la cetrería.
- Actividades y eventos.
- Noticias o novedades.
- Comisión directiva.
- Galería.
- Información para asociarse.
- Contacto y redes sociales.
- Aviso de privacidad.
- Diseño adaptado a móvil, tablet y escritorio.

No incluye:

- Inicio de sesión.
- Base de datos de socios.
- Edición de contenido desde panel.
- Pagos.
- Carnet virtual.

### Fase 2 — Autenticación y gestión de socios

Incluye:

- Inicio y cierre de sesión.
- Recuperación segura de acceso.
- Alta, consulta, edición y baja lógica de socios.
- Estados de socio.
- Historial básico de cambios.
- Área privada del socio.
- Gestión de usuarios y roles.

### Fase 3 — Panel administrativo

Incluye:

- Tablero general.
- Búsqueda y filtros de socios.
- Gestión de comisión directiva.
- Administración de estados y vigencias.
- Auditoría de acciones relevantes.
- Exportaciones autorizadas.

### Fase 4 — Carnet virtual

Incluye:

- Emisión individual de carnet.
- Número de socio.
- Fotografía aprobada.
- Fecha de emisión y vencimiento.
- Estado: válido, vencido, suspendido o revocado.
- Código QR con identificador no predecible.
- Página pública de verificación con datos mínimos.
- Posibilidad de revocación y reemisión.

### Fase 5 — Evoluciones posibles

Fuera del compromiso inicial:

- Cuotas y pagos.
- Inscripciones a eventos.
- Certificados.
- Biblioteca o contenido educativo.
- Aplicación móvil.
- Integraciones con sistemas externos.

## 4. Roles preliminares

### Visitante

Puede acceder únicamente al contenido público y verificar un carnet mediante su enlace público.

### Socio

Puede consultar y solicitar correcciones de su información, visualizar su estado y acceder a su carnet cuando esté habilitado.

### Operador administrativo

Puede consultar y actualizar datos operativos de socios conforme a permisos asignados.

### Comisión directiva

Puede consultar información institucional y ejecutar funciones específicas según su cargo y autorización.

### Administrador

Puede gestionar socios, carnets, contenidos y usuarios dentro de los permisos definidos.

### Superadministrador

Puede asignar roles sensibles y administrar configuración crítica. Su uso debe ser limitado y auditable.

> Los permisos definitivos deberán especificarse mediante una matriz RBAC antes de implementar autenticación.

## 5. Entidades preliminares

### Member

- Identificador interno.
- Número de socio.
- Nombre y apellido.
- Tipo y número de documento.
- Fecha de nacimiento, si corresponde legal y operativamente.
- Correo electrónico.
- Teléfono.
- Localidad y provincia.
- Fecha de ingreso.
- Estado.
- Observaciones internas con acceso restringido.
- Fechas de creación y modificación.

### User

- Identificador.
- Socio asociado opcional.
- Correo de acceso.
- Estado de la cuenta.
- Roles.
- Último acceso.

### BoardPosition

- Cargo.
- Persona asociada.
- Fecha de inicio.
- Fecha de finalización.
- Estado de publicación.
- Orden de visualización.

### DigitalCredential

- Identificador interno.
- Identificador público aleatorio.
- Socio asociado.
- Fecha de emisión.
- Fecha de vencimiento.
- Estado.
- Fecha y motivo de revocación.
- Versión de credencial.

### AuditEvent

- Actor.
- Acción.
- Entidad afectada.
- Identificador de entidad.
- Fecha y hora.
- Metadatos mínimos necesarios.

## 6. Reglas de negocio preliminares

1. Cada socio debe tener un número de socio único.
2. La baja de un socio será lógica; no se eliminarán registros históricos sin un procedimiento explícito.
3. Solo usuarios autorizados podrán modificar el estado de un socio.
4. Un socio no podrá modificar directamente campos administrativos sensibles.
5. Solo podrá existir un carnet vigente por socio, salvo excepción documentada.
6. Revocar un carnet no eliminará su historial.
7. El QR no contendrá datos personales legibles; contendrá una URL o token público seguro.
8. La verificación pública mostrará únicamente los datos aprobados por ACA.
9. Los permisos se comprobarán en servidor para cada operación protegida.
10. Los cambios críticos deberán generar eventos de auditoría.

## 7. Requisitos no funcionales

### Responsive

- Enfoque mobile-first.
- Compatibilidad con anchos desde 320 px.
- Navegación móvil usable sin desbordamientos horizontales.
- Contenido legible en tablet y escritorio.

### Accesibilidad

- HTML semántico.
- Navegación mediante teclado.
- Foco visible.
- Texto alternativo en imágenes relevantes.
- Contraste suficiente.
- Formularios con etiquetas y mensajes de error asociados.

### Rendimiento

- Optimización de imágenes.
- Carga diferida cuando sea apropiado.
- Evitar JavaScript innecesario en páginas públicas.
- Objetivo inicial: buen desempeño en Core Web Vitals, medido antes de cada lanzamiento.

### Seguridad

- TypeScript estricto.
- Validación de entradas en servidor.
- Protección contra acceso horizontal entre socios.
- Principio de mínimo privilegio.
- Sesiones seguras.
- Rate limiting en autenticación y verificación pública cuando corresponda.
- Secretos únicamente en variables de entorno.
- Dependencias auditadas y actualizadas.

### Privacidad

- Recolectar solamente datos necesarios.
- Separar datos públicos, privados y administrativos.
- Definir plazos y procedimientos de conservación.
- Registrar quién accede o modifica datos sensibles cuando corresponda.
- No publicar listados de socios.

## 8. Arquitectura objetivo

- Aplicación web: Next.js con App Router y TypeScript.
- Interfaz: React con componentes accesibles y responsive.
- Base de datos: PostgreSQL.
- Validación: Zod o herramienta equivalente aprobada mediante ADR.
- Autenticación: proveedor por definir antes de Fase 2.
- Almacenamiento de imágenes: servicio privado con URLs controladas.
- Despliegue: por definir mediante ADR.

Se utilizará inicialmente un monolito modular. Los módulos de dominio se mantendrán separados para permitir futuras APIs o clientes móviles.

## 9. Estructura funcional propuesta

```text
src/
├── app/
│   ├── (public)/
│   ├── (member)/
│   ├── admin/
│   └── api/
├── components/
├── features/
│   ├── members/
│   ├── board/
│   ├── credentials/
│   ├── authentication/
│   └── administration/
├── lib/
├── server/
├── types/
└── tests/
```

## 10. Navegación pública preliminar

- Inicio.
- La asociación.
- Cetrería.
- Actividades.
- Noticias.
- Galería.
- Asociarse.
- Contacto.
- Acceso de socios, visible pero no habilitado hasta Fase 2.

## 11. Criterios de aceptación de la Fase 1

1. El sitio funciona sin desplazamiento horizontal en 320 px, 768 px y 1440 px.
2. El menú es completamente utilizable con teclado y en dispositivos táctiles.
3. Todas las páginas públicas poseen título, descripción y jerarquía correcta de encabezados.
4. La información institucional marcada como pendiente no se publica como definitiva.
5. Los formularios validan campos y presentan errores comprensibles.
6. Los datos de contacto se obtienen desde configuración central y no se duplican en múltiples componentes.
7. El proyecto supera lint, verificación de tipos y build de producción.
8. Las rutas principales poseen pruebas mínimas.
9. No se incluyen datos reales de socios en código, fixtures ni capturas.
10. El repositorio contiene README, AGENTS.md, especificaciones y ADR iniciales.

## 12. Contenido pendiente de ACA

- Logotipo oficial y variantes autorizadas.
- Paleta de colores institucional.
- Tipografías, si existen.
- Historia institucional aprobada.
- Misión, visión y objetivos oficiales.
- Comisión directiva vigente.
- Correo, teléfono, domicilio y redes oficiales.
- Estatuto o texto público autorizado.
- Requisitos y proceso para asociarse.
- Fotografías con derechos de publicación.
- Política de privacidad y responsable de datos.

## 13. Preguntas abiertas

- ¿Quién podrá dar de alta a un socio?
- ¿Cómo se asigna el número de socio?
- ¿Qué estados de socio existen y qué efectos tienen?
- ¿La vigencia del carnet depende del pago de cuotas?
- ¿Qué datos deben verse en el carnet?
- ¿Qué datos deben verse al verificar el QR?
- ¿Qué cargos administrativos necesitan acceso?
- ¿La comisión se publica automáticamente o requiere aprobación?
- ¿Se necesitan delegaciones provinciales?
- ¿Habrá menores de edad registrados como socios?
- ¿Se almacenarán documentos o certificados?

## 14. Estrategia de desarrollo

Cada funcionalidad deberá contar con:

1. Especificación propia.
2. Casos de uso.
3. Reglas de negocio.
4. Modelo de datos afectado.
5. Permisos.
6. Criterios de aceptación.
7. Plan de pruebas.
8. Pull request pequeño y revisable.

## 15. Primer incremento

El primer incremento será `SPEC-001 — Sitio institucional responsive`, centrado en:

- Sistema visual provisional.
- Header y navegación responsive.
- Hero de inicio.
- Presentación de la asociación.
- Secciones de cetrería, actividades y asociarse.
- Footer y contacto.
- Datos centralizados en archivos de configuración.
- Contenido provisional claramente marcado.
