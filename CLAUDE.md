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

- **`docs/`**: el apunte del curso propiamente dicho, un archivo `.md` por
  módulo (`modulo-0.md`, `modulo-1.md`, ...) más `docs/intro.md` como portada
  (sirve en la raíz del sitio vía `slug: /`). Es la fuente que Docusaurus
  convierte en sitio estático; el orden del menú lateral lo define
  `sidebar_position` en el frontmatter de cada doc (autogenerado, ver
  `sidebars.ts`).
- **README.md**: portada corta del repo en GitHub — resumen, link al sitio
  publicado, índice de módulos con checklist, e instrucciones para correr el
  sitio en local. No repite el contenido de cada módulo, eso vive en `docs/`.
- **docusaurus.config.ts** / **sidebars.ts**: configuración del sitio
  (Docusaurus, tema, idioma `es`, navegación, datos de GitHub Pages).
- **CLAUDE.md** (este archivo): memoria de proyecto para Claude. No es apunte
  para el usuario — son las reglas de trabajo y el estado de avance, para que
  cualquier sesión nueva (con o sin memoria automática) pueda retomar sin
  perder contexto.

Un módulo se da por cerrado cuando existe su `docs/modulo-N.md` con el
`sidebar_position` correcto y está linkeado desde el índice del README.

**Nota de historia**: el sitio arrancó armado con MkDocs Material (ver
Módulo 6 original) y se migró por completo a Docusaurus a pedido del usuario
por estética — la migración descartó el tooling *y* el contenido anterior de
MkDocs, reescribiendo los módulos 0, 1 y 6 desde cero sobre la nueva base. Si
en algún momento se referencia `mkdocs.yml`, `requirements.txt` o `.venv/`,
son restos de una versión anterior del repo: ya no existen.

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
- [x] Módulo 2 — Mejores prácticas de uso: prompting (contexto, especificidad,
      iterar en pasos chicos), modos de permiso (manual/ask, auto-accept,
      full auto) y Plan Mode (cuándo conviene vs. revisar el diff después).
- [ ] Módulo 3 — Memoria de proyecto: CLAUDE.md y memoria automática —
      **siguiente**.
- [ ] Módulo 4 — CLAUDE.md exportable para trabajo colaborativo.
- [ ] Módulo 5 — Buenas prácticas de repositorio personal (git, estructura,
      commits).
- [x] Módulo 6 — Publicar en GitHub y flujo de trabajo final: el sitio corre
      sobre **Docusaurus** (`docusaurus.config.ts`, `sidebars.ts`, `docs/`,
      `node_modules` gitignoreado) y el workflow
      `.github/workflows/deploy.yml` publica a GitHub Pages con el mecanismo
      nativo (`actions/deploy-pages`), no con rama `gh-pages`. **Falta que el
      usuario**: (1) resolver auth SSH/HTTPS a GitHub, (2) hacer el primer
      `git push`, (3) en Settings → Pages, elegir **"GitHub Actions"** como
      fuente (no "Deploy from a branch"). Detalle paso a paso en
      `docs/modulo-6.md`.
      Se adelantó este módulo fuera de orden porque el usuario pidió probar
      GitHub Pages; los Módulos 2 a 5 siguen pendientes. Originalmente se
      armó con MkDocs Material y se migró a Docusaurus en una sesión
      posterior porque al usuario no le convenció la estética de MkDocs — la
      migración fue completa (tooling + contenido reescrito desde cero).

## Pendientes conocidos (no resolver salvo que el usuario lo pida)

- El `user.email` local del repo: verificar con `git config user.email` antes
  de asumir cuál está seteado — el usuario lo maneja él mismo, no tocar.
- No está instalado `gh` CLI; el push a GitHub va a ir por SSH o HTTPS con
  credential manager (se define en el Módulo 6).
- Migración de MkDocs a Docusaurus (2026-09-20): quedan sin commitear los
  cambios (borrado de `mkdocs.yml`/`docs/`/`requirements.txt`/`.venv`/workflow
  viejo, alta de todo el scaffold de Docusaurus). No commitear sin que el
  usuario lo pida explícitamente.

## Cómo continuar si esta sesión se corta

1. Leer este archivo.
2. Leer el índice del README.md para ver qué módulos están tildados.
3. Retomar en el primer módulo sin tildar, o en el que esté marcado "en
   curso" en la sección de estado de avance de arriba.
