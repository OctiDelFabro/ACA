# AGENTS.md — Página ACA

## Propósito

Este repositorio contiene la web institucional y el futuro sistema de gestión de la Asociación Civil Cetreros Argentinos.

## Regla principal

Antes de implementar una tarea, leer la especificación correspondiente en `docs/specs/`. No inventar requisitos, campos, permisos ni reglas de negocio que no estén documentados.

## Stack objetivo

- Next.js con App Router.
- React.
- TypeScript en modo estricto.
- PostgreSQL.
- Validación de entradas con Zod.
- CSS responsive y accesible; Tailwind CSS podrá utilizarse tras su ADR.
- Pruebas unitarias y de integración.
- Pruebas end-to-end para flujos críticos.

## Convenciones

- El idioma de interfaz y documentación funcional es español.
- El código, identificadores y nombres de archivos técnicos se escriben en inglés.
- Evitar `any`; justificar cualquier excepción.
- Validar toda entrada externa en servidor.
- Nunca confiar permisos únicamente al frontend.
- No almacenar secretos en el repositorio.
- No exponer DNI, domicilio, teléfono, correo u otros datos personales en páginas públicas.
- Las migraciones de base de datos deben ser versionadas.
- Los cambios de esquema deben actualizar `docs/architecture/data-model.md`.

## Flujo de trabajo

1. Leer la especificación.
2. Identificar criterios de aceptación.
3. Proponer cambios mínimos.
4. Implementar.
5. Ejecutar lint, verificación de tipos, pruebas y build.
6. Actualizar documentación cuando corresponda.
7. Preparar un pull request con resumen, pruebas y riesgos.

## Definition of Done

Una tarea se considera terminada cuando:

- Cumple los criterios de aceptación.
- No introduce errores de TypeScript.
- Supera lint y pruebas.
- Mantiene diseño responsive.
- Mantiene accesibilidad básica por teclado y lectores de pantalla.
- No debilita controles de autorización o privacidad.
- Incluye documentación si cambia comportamiento o arquitectura.

## Restricciones de dominio

- La información pública de la comisión directiva debe ser aprobada por ACA.
- El estado de socio y carnet debe provenir del servidor.
- Los códigos QR de carnets deben usar identificadores públicos no predecibles.
- Un carnet revocado o vencido debe indicarse claramente como no válido.
- Toda acción administrativa relevante debe poder auditarse.
