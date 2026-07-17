# ADR-003 — PostgreSQL

- **Estado:** Propuesto
- **Fecha:** 2026-07-17

## Decisión propuesta

Utilizar PostgreSQL como base de datos principal.

## Motivo

El dominio requiere integridad referencial, restricciones, consultas administrativas, auditoría y crecimiento ordenado.

## Consecuencias

- El esquema debe gestionarse mediante migraciones.
- Se definirán índices, restricciones y políticas de acceso antes de almacenar datos reales.
- La elección de proveedor se resolverá en un ADR separado.
