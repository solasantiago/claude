---
sidebar_position: 4
---

# Módulo 2 — Mejores prácticas de uso

## Apunte

### Prompting

Claude Code no adivina intención de la nada — cuanto más contexto concreto
le des, mejor la respuesta. Algunas ideas que ya usamos en este mismo curso:

- **Ser específico sobre el alcance**: "cambiá el color primario a indigo"
  es mejor que "mejorá los colores".
- **Dar contexto de por qué, no solo qué**: ayuda a que la solución encaje
  con la intención real en vez de una lectura literal del pedido.
- **Iterar en pasos chicos**: pedir un cambio, revisarlo, pedir el
  siguiente — en vez de un pedido gigante de una sola vez. Así cada paso es
  fácil de revisar y corregir.
- **Dejar que pregunte cuando hay ambigüedad real**: si un pedido admite más
  de una interpretación razonable (por ejemplo, "descartemos todo" — ¿incluye
  el contenido o solo la config?), es mejor que pregunte en vez de asumir.

### Modos de permiso

Claude Code no ejecuta cualquier cosa sin control — hay distintos modos de
cuánto necesita tu aprobación antes de actuar:

- **Manual/ask** (default más conservador): pide confirmación antes de cada
  herramienta que no sea de solo lectura (editar archivos, correr comandos).
- **Auto-accept editar** en un directorio o para ciertas herramientas: deja
  de preguntar para acciones de bajo riesgo y reversibles (lectura, edición
  de archivos), pero sigue pidiendo confirmación para lo destructivo o
  irreversible (borrar, hacer push, etc.).
- **Full auto / "dangerously skip permissions"**: no pregunta nada. Útil en
  entornos aislados (un sandbox, un contenedor descartable), pero arriesgado
  en un repo real con acceso a internet o credenciales.

La elección de modo es un trade-off entre velocidad y control: más
automático es más rápido pero exige más confianza en que las instrucciones
de contexto (como este `CLAUDE.md`) sean correctas y suficientes.

### Plan Mode

Plan Mode es un modo de solo lectura: Claude puede explorar el código, leer
archivos, buscar, pero **no puede editar ni ejecutar nada** hasta que
presente un plan y vos lo apruebes explícitamente.

Conviene usarlo cuando:

- El cambio es grande o toca varios archivos y querés ver el enfoque antes
  de que se ejecute.
- No tenés claro de antemano qué archivos se van a tocar.
- Querés poder pedir ajustes al plan sin haber gastado ya una ronda de
  ediciones.

No hace falta para cambios chicos y bien acotados (como los que venimos
haciendo en `docs/`), donde revisar el diff después de hecho es más rápido
que aprobar un plan antes.

## Ejercicio práctico

1. Activá Plan Mode (en el CLI, con el atajo o flag correspondiente; en la
   extensión de VS Code, desde el selector de modo) y pedile a Claude Code
   un cambio que toque más de un archivo del repo — por ejemplo, "agregá una
   sección de créditos al final de cada módulo". Miren el plan antes de
   aprobarlo.
2. Compará ese flujo con pedir el mismo tipo de cambio en modo normal
   (sin Plan Mode) y revisar el diff después. ¿Cuál te resultó más cómodo
   para este caso?
3. Probá reformular un pedido ambiguo a propósito (por ejemplo, "mejorá el
   README") y observá si Claude pregunta para acotar el alcance o asume algo
   por su cuenta. Si asume, reformulá el prompt para que sea más específico
   y notá la diferencia en el resultado.
