# Workshop: Claude Code desde cero (VS Code + Terminal)

Notas de curso que voy armando mientras aprendo a usar Claude Code. Este README es
"vivo": cada módulo se agrega cuando lo cerramos en la sesión de chat, así que el
archivo va creciendo en orden. La idea final es que este repo sea mi base de
conocimiento personal y quede publicado en GitHub.

## Índice de módulos

- [x] Módulo 0 — Setup del repo
- [x] Módulo 1 — Qué es Claude Code: extensión de VS Code vs. terminal
- [ ] Módulo 2 — Mejores prácticas de uso (prompting, modos de permiso, Plan Mode)
- [ ] Módulo 3 — Memoria de proyecto: CLAUDE.md y memoria automática
- [ ] Módulo 4 — CLAUDE.md exportable para trabajo colaborativo
- [ ] Módulo 5 — Buenas prácticas de repositorio personal (git, estructura, commits)
- [ ] Módulo 6 — Publicar en GitHub y flujo de trabajo final

---

## Módulo 0 — Setup del repo

**Objetivo:** tener un repo git local, listo para ir documentando cada módulo.

Lo que se hizo:
- `git init` en `/home/ssola/sandbox`, branch renombreada a `main`.
- Se configuró el email local del repo (`santiagoms.ss@gmail.com`) distinto del
  global (`santiago.sola@coto.com.ar`), porque este es un repo **personal**, no
  de trabajo. Esto se hace con `git config user.email "..."` (sin `--global`),
  que sobreescribe la identidad solo para este repo.
- Se crea este `README.md` como bitácora del curso.
- Se va a crear un `CLAUDE.md` como memoria base del proyecto (Módulo 3 y 4).
- Se agregó el remoto `origin` apuntando a
  [github.com/solasantiago/claude](https://github.com/solasantiago/claude).
  Todavía no se hizo push: falta configurar cómo se autentica esa cuenta desde
  esta máquina (no hay `gh` CLI instalado, así que va a ser vía HTTPS con
  credential manager o vía SSH — se define en el Módulo 6).

**Por qué importa la identidad de git:** cada commit queda firmado con el
`user.name`/`user.email` configurados. Si tenés varios repos (laburo, personal,
open source) conviene setear el email *por repo* en vez de global, para no
mezclar tu email laboral con tus proyectos personales quen public en GitHub.

---

## Módulo 1 — Qué es Claude Code: extensión de VS Code vs. terminal

**Objetivo:** entender qué es Claude Code, sus dos formas de uso (extensión de
VS Code y CLI en terminal), y dejar la terminal de Ubuntu andando para las
próximas sesiones.

### Qué es Claude Code

Claude Code es un agente de asistencia para programar: no es solo un chat que
responde texto, sino que puede **leer y escribir archivos, correr comandos de
terminal, usar git, buscar en el código, etc.**, dentro del proyecto donde se
lo invoca. La diferencia con un chat común es que actúa sobre el repo real,
con las herramientas (`Read`, `Edit`, `Bash`, ...) que tiene habilitadas.

Existen dos formas equivalentes de usarlo, mismo motor por debajo:

| | Extensión de VS Code | CLI en terminal |
|---|---|---|
| Dónde corre | Panel lateral del editor | Terminal (bash/zsh) |
| Qué ves | Chat + diffs integrados en el editor | Todo en texto plano en la consola |
| Cuándo conviene | Trabajo interactivo revisando código a la vez | Automatización, scripts, sesiones remotas/SSH, cuando no tenés editor gráfico |
| Memoria / contexto | La misma: lee `CLAUDE.md` del proyecto en ambos casos | ídem |

Lo importante: **el "cerebro" y las reglas de memoria (`CLAUDE.md`) son las
mismas** en los dos casos. Lo que cambia es la interfaz.

### Claude Code desde la terminal de Ubuntu

Instalación (requiere Node.js instalado):

```bash
npm install -g @anthropic-ai/claude-code
```

Verificar que quedó instalado:

```bash
claude --version
```

Formas de uso desde la terminal:

- **Modo interactivo** (equivalente al panel de VS Code, pero en la consola):
  ```bash
  cd /ruta/al/proyecto
  claude
  ```
  Abre una sesión de chat dentro de la terminal, en el directorio actual.

- **Modo "one-shot"** (un solo pedido, sin quedar en sesión interactiva):
  ```bash
  claude "explicame qué hace este proyecto"
  ```
  Útil para scripts o para pedidos puntuales rápidos.

- **Dentro de la sesión interactiva** existen *slash commands* como `/help`,
  `/clear` (limpiar contexto), `/config` (ajustes), y los que cada proyecto
  agregue como skills propias.

### Ejercicio práctico

1. Abrí una terminal de Ubuntu (fuera de VS Code).
2. Corré `claude --version` para confirmar la instalación (si da "command not
   found", corré el `npm install -g` de arriba primero).
3. Pará en el directorio del repo (`cd /home/ssola/sandbox/claude`) y corré
   `claude` en modo interactivo.
4. Probá pedirle algo simple, por ejemplo: *"leé el README.md de este repo y
   contame en qué módulo vamos"*. Confirmá que responde usando el contexto
   real del `CLAUDE.md`/`README.md` (no una respuesta genérica).
5. Salí de la sesión con `Ctrl+C` (dos veces) o escribiendo `/exit`.

> Nota: los cambios que Claude haga en modo terminal son sobre los mismos
> archivos del repo — no es un entorno aislado distinto del que usás desde VS
> Code.

---
