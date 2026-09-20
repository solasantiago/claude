---
sidebar_position: 3
---

# Módulo 1 — Claude Code: extensión de VS Code vs. terminal

## Apunte

Claude Code no es solo un chat: es un agente con acceso real a herramientas
(lectura/escritura de archivos, shell, git, búsqueda en el código), y podés
usarlo desde dos superficies distintas sobre el mismo motor:

- **Extensión de VS Code**: Claude Code integrado al editor. Ves los diffs
  propuestos inline, los cambios de archivo en la UI del editor, y podés
  aprobar o rechazar ediciones con la misma interacción que usarías para
  revisar un PR.
- **Terminal**: el CLI (`claude`) corriendo directo en una shell (en este
  caso, terminal de Ubuntu/WSL). Más "crudo" en apariencia, pero más
  flexible: se puede invocar desde scripts, hooks, CI, o conectarse por SSH a
  un servidor remoto donde no hay editor gráfico.

Ambas superficies comparten el mismo modelo, las mismas herramientas y el
mismo `CLAUDE.md` de contexto del proyecto — la elección es de flujo de
trabajo, no de capacidad.

## Ejercicio práctico

1. Si todavía no la tenés, instalá la extensión de Claude Code en VS Code y
   abrí este repo con ella.
2. Pedile el mismo cambio chico (por ejemplo, corregir una errata en el
   README) primero desde la extensión y después desde la terminal con
   `claude`.
3. Compará la experiencia: cómo se ve el diff propuesto en cada caso, y qué
   tan cómodo te resulta aprobar cambios en una superficie vs. la otra.
