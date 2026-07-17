# ADR-001 — TypeScript

- **Estado:** Aceptado
- **Fecha:** 2026-07-17

## Decisión

Utilizar TypeScript con configuración estricta para toda la aplicación.

## Motivo

El sistema manejará entidades y permisos complejos. El tipado estático reduce errores de integración, mejora refactors y brinda mejores restricciones a los cambios generados con asistencia de Codex.

## Consecuencias

- Mayor disciplina inicial.
- Menos errores por estructuras inconsistentes.
- Se evitará `any` salvo excepción justificada.
