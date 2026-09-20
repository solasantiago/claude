# CLAUDE.md — Memoria del proyecto

Este archivo es la memoria de contexto que Claude debe leer al empezar a trabajar
en este repo. El repo **es** el workshop: un curso incremental para aprender a
usar Claude (extensión VS Code + Claude Code en terminal) como asistente de
desarrollo, documentado en [README.md](README.md) a medida que se avanza.

## Qué es este proyecto

Un curso personal, en formato de apunte vivo, que va de cero a un uso avanzado
de Claude como asistente en un proyecto real. El "proyecto real" es este mismo
repositorio: se aprende haciendo, y cada cosa que se prueba o se decide queda
documentada en el README como si fuera una clase.

- **README.md**: el apunte del curso. Tiene un índice de módulos al principio
  (checklist) y después el desarrollo de cada módulo, en orden secuencial. Se
  completa incrementalmente: un módulo se da por cerrado recién cuando su
  sección en el README está escrita.
- **CLAUDE.md** (este archivo): memoria de proyecto para Claude. No es apunte
  para el usuario — son las reglas de trabajo y el estado de avance, para que
  cualquier sesión nueva (con o sin memoria automática) pueda retomar sin
  perder contexto.

## Reglas de trabajo en este repo

- **No hacer `git push` nunca**, salvo pedido explícito y puntual en el
  momento. El usuario hace push manualmente desde Source Control.
- **No crear ni escribir archivos fuera de este directorio**
  (`/home/ssola/sandbox/claude`), salvo el uso del scratchpad de sesión para
  archivos temporales que no pertenecen al repo.
- El repo es **personal**, separado del repo/identidad de trabajo. La
  identidad de git (`user.email`) para este repo la maneja el usuario
  directamente (no asumir que está seteada ni configurarla sin que lo pida).
- Los commits, cuando el usuario los pida, los arma Claude; el push lo hace
  siempre el usuario.
- Formato de aprendizaje: cada módulo combina **apunte conceptual corto +
  ejercicio práctico** para hacer en el momento (comando a correr, prompt a
  probar, etc.), no solo teoría.
- El README debe quedar legible y prolijo como para que otra persona pueda
  clonar el repo y sumarse a colaborar o seguir el curso.

## Estado de avance (actualizar cada vez que se cierra o abre un módulo)

- [x] Módulo 0 — Setup del repo (repo git local, README inicial, remoto
      `origin` configurado a `github.com/solasantiago/claude`, sin push aún).
- [x] Módulo 1 — Qué es Claude Code: extensión de VS Code vs. terminal
      (incluye uso desde terminal de Ubuntu).
- [ ] Módulo 2 — Mejores prácticas de uso (prompting, modos de permiso, Plan
      Mode) — **siguiente**.
- [ ] Módulo 3 — Memoria de proyecto: CLAUDE.md y memoria automática.
- [ ] Módulo 4 — CLAUDE.md exportable para trabajo colaborativo.
- [ ] Módulo 5 — Buenas prácticas de repositorio personal (git, estructura,
      commits).
- [ ] Módulo 6 — Publicar en GitHub y flujo de trabajo final.

## Pendientes conocidos (no resolver salvo que el usuario lo pida)

- El `user.email` local del repo todavía no está seteado a
  `santiagoms.ss@gmail.com` (usa el global `santiago.sola@coto.com.ar`). El
  usuario dijo que lo resuelve él mismo — no tocar.
- No hay commits todavía en el repo (`README.md` está untracked). No commitear
  sin que el usuario lo pida.
- No está instalado `gh` CLI; el push a GitHub va a ir por SSH o HTTPS con
  credential manager (se define en el Módulo 6).

## Cómo continuar si esta sesión se corta

1. Leer este archivo.
2. Leer el índice del README.md para ver qué módulos están tildados.
3. Retomar en el primer módulo sin tildar, o en el que esté marcado "en
   curso" en la sección de estado de avance de arriba.
