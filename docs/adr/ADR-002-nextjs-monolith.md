# ADR-002 — Monolito modular con Next.js

- **Estado:** Propuesto
- **Fecha:** 2026-07-17

## Decisión propuesta

Construir inicialmente la plataforma como una aplicación Next.js con App Router, separada internamente por dominios.

## Motivo

Permite entregar el sitio público y evolucionar hacia autenticación, administración y carnet virtual sin mantener desde el inicio múltiples aplicaciones o servicios.

## Consecuencias

- Despliegue y desarrollo inicial más simples.
- Deben respetarse límites internos para evitar acoplamiento.
- Una API independiente podrá extraerse cuando exista una necesidad real.
