# Módulo 0 — Setup del repo

**Objetivo:** tener un repo git local, listo para ir documentando cada módulo.

Lo que se hizo:

- `git init` en `/home/ssola/sandbox/claude`, branch renombrada a `main`.
- Se decidió configurar el email local del repo (`santiagoms.ss@gmail.com`)
  distinto del global (`santiago.sola@coto.com.ar`), porque este es un repo
  **personal**, no de trabajo. Esto se hace con `git config user.email "..."`
  (sin `--global`), que sobreescribe la identidad solo para este repo.
- Se creó un `README.md` como bitácora inicial del curso (luego migrado a este
  sitio de MkDocs en el Módulo 6).
- Se creó un `CLAUDE.md` como memoria base del proyecto (Módulo 3 y 4).
- Se agregó el remoto `origin` apuntando a
  [github.com/solasantiago/claude](https://github.com/solasantiago/claude).
  Todavía no se hizo push: falta configurar cómo se autentica esa cuenta desde
  esta máquina (no hay `gh` CLI instalado, así que va a ser vía HTTPS con
  credential manager o vía SSH — se define en el Módulo 6).

**Por qué importa la identidad de git:** cada commit queda firmado con el
`user.name`/`user.email` configurados. Si tenés varios repos (laburo, personal,
open source) conviene setear el email *por repo* en vez de global, para no
mezclar tu email laboral con tus proyectos personales que publiques en GitHub.
