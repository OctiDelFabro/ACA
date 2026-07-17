# Arquitectura inicial

## Estilo

Monolito modular en Next.js. La interfaz pública, el área privada, el panel administrativo y las operaciones de servidor vivirán en una sola aplicación, pero separados por dominios y permisos.

## Límites de dominio

- `public-content`: contenido institucional y navegación pública.
- `members`: información y estado de socios.
- `board`: cargos y períodos de comisión directiva.
- `credentials`: emisión, revocación y verificación de carnets.
- `identity`: usuarios, sesiones y roles.
- `administration`: operaciones internas y auditoría.

## Flujos de confianza

- El navegador nunca determina permisos finales.
- Las operaciones protegidas se autorizan en servidor.
- La base de datos aplica restricciones de unicidad e integridad.
- La verificación pública del carnet accede a una vista de datos mínimos.

## Decisiones pendientes

- Proveedor de autenticación.
- ORM o acceso SQL.
- Hospedaje.
- Servicio de almacenamiento de imágenes.
- Servicio de correo transaccional.
