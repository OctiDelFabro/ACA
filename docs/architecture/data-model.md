# Modelo de datos preliminar

Este documento es conceptual. No habilita todavía la creación del esquema productivo.

## Relaciones principales

- Un `Member` puede tener cero o un `User` asociado inicialmente.
- Un `Member` puede ocupar cero o varios `BoardPosition` a lo largo del tiempo.
- Un `Member` puede tener varios `DigitalCredential` históricos, pero como regla general solo uno vigente.
- Un `User` puede tener uno o varios roles.
- Las operaciones críticas generan `AuditEvent`.

## Restricciones mínimas

- `Member.memberNumber` único.
- `DigitalCredential.publicId` único y no secuencial.
- Fechas de períodos coherentes.
- Eliminación lógica para socios y credenciales.
