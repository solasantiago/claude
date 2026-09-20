# Módulo 1 — Qué es Claude Code: extensión de VS Code vs. terminal

**Objetivo:** entender qué es Claude Code, sus dos formas de uso (extensión de
VS Code y CLI en terminal), y dejar la terminal de Ubuntu andando para las
próximas sesiones.

## Qué es Claude Code

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

## Claude Code desde la terminal de Ubuntu

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

## Ejercicio práctico

1. Abrí una terminal de Ubuntu (fuera de VS Code).
2. Corré `claude --version` para confirmar la instalación (si da "command not
   found", corré el `npm install -g` de arriba primero).
3. Parate en el directorio del repo (`cd /home/ssola/sandbox/claude`) y corré
   `claude` en modo interactivo.
4. Probá pedirle algo simple, por ejemplo: *"leé el README.md de este repo y
   contame en qué módulo vamos"*. Confirmá que responde usando el contexto
   real del `CLAUDE.md` (no una respuesta genérica).
5. Salí de la sesión con `Ctrl+C` (dos veces) o escribiendo `/exit`.

!!! note
    Los cambios que Claude haga en modo terminal son sobre los mismos archivos
    del repo — no es un entorno aislado distinto del que usás desde VS Code.
