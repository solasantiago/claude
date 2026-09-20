---
sidebar_position: 2
---

# Módulo 0 — Setup del repo

## Apunte

Antes de tocar Claude Code, el curso necesita un lugar donde vivir: un
repositorio git personal, separado de cualquier repo de trabajo, donde cada
módulo se documenta a medida que se cierra.

Lo mínimo para arrancar:

- Un repo git local (`git init`), con un `README.md` que explique de qué va
  el proyecto.
- Un remoto en GitHub (`origin`) apuntando a `github.com/<usuario>/<repo>`,
  configurado pero **sin necesidad de hacer push todavía** — el push queda
  para cuando el contenido esté listo para publicarse.
- Identidad de git separada de la de trabajo: el `user.email` de este repo
  no tiene por qué ser el mismo que el de tu organización.

## Ejercicio práctico

1. Creá un directorio nuevo y corré `git init`.
2. Escribí un `README.md` corto explicando el propósito del repo.
3. Agregá el remoto: `git remote add origin git@github.com:<usuario>/<repo>.git`
   (o la URL HTTPS si preferís ese flujo).
4. Verificá con `git remote -v` que quedó bien configurado, sin hacer push
   todavía.
