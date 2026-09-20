---
sidebar_position: 5
---

# Módulo 6 — Publicar en GitHub y flujo de trabajo final

## Apunte

El apunte del curso vive como markdown en `docs/`, pero para que sea
navegable como sitio necesita un generador de sitio estático. Se usa
[Docusaurus](https://docusaurus.io/) (React + TypeScript):

- `docusaurus.config.ts`: configuración del sitio — título, idioma (`es`),
  organización/repo de GitHub, navbar y footer.
- `sidebars.ts`: define cómo se arma el menú lateral (acá, autogenerado a
  partir del orden `sidebar_position` de cada doc).
- `docs/`: el contenido, un `.md` por módulo.
- `.github/workflows/`: el workflow que buildea el sitio y lo publica en
  GitHub Pages en cada push a `main`, usando el mecanismo nativo de Pages
  (`actions/deploy-pages`), no una rama `gh-pages` separada.

## Ejercicio práctico

1. Corré el sitio en local:

   ```bash
   npm install
   npm start
   ```

2. Confirmá que el módulo que estés editando aparece en el menú lateral con
   el `sidebar_position` correcto.
3. Para ver el build de producción tal cual queda publicado:

   ```bash
   npm run build
   npm run serve
   ```

4. En GitHub, andá a **Settings → Pages** y configurá la fuente como
   **GitHub Actions** (no "Deploy from a branch") para que el workflow de
   `deploy-pages` pueda publicar.
