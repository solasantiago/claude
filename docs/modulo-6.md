# Módulo 6 — Publicar en GitHub y flujo de trabajo final

**Objetivo:** convertir el apunte en un sitio navegable (con búsqueda,
sidebar, tema claro/oscuro) publicado en GitHub Pages, sin perder la
practicidad de escribir en Markdown.

## Por qué MkDocs Material en vez de solo un README

Un `README.md` gigante se renderiza bien en GitHub, pero no tiene navegación
por secciones, búsqueda, ni un formato tipo "documentación". La alternativa
evaluada fue armar directamente una página HTML a mano — se descartó porque
implicaba mantener dos fuentes de verdad (el Markdown de trabajo y el HTML
publicado) y perder la edición rápida módulo a módulo.

**MkDocs Material** es un generador de sitio estático: toma archivos
`.md` de una carpeta `docs/` y genera un sitio HTML completo (navegación,
buscador, tema) sin tocar el contenido fuente. El sitio publicado siempre es
el resultado de un *build*, nunca se genera "al vuelo" cuando alguien abre la
página.

## Cómo se generó en esta sesión

1. Entorno virtual de Python dentro del repo, para no instalar nada global:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   pip install mkdocs-material
   ```

2. Estructura de contenido movida a `docs/` (un archivo `.md` por módulo) y
   configuración en `mkdocs.yml` en la raíz del repo.

3. Previsualización local (se actualiza en vivo mientras se edita):

   ```bash
   mkdocs serve
   ```

   Sirve el sitio en `http://127.0.0.1:8000`.

4. Build de producción (genera la carpeta `site/`, no se versiona en git):

   ```bash
   mkdocs build
   ```

## Publicación automática con GitHub Actions

En vez de correr el build a mano antes de cada push, se agregó un workflow
(`.github/workflows/docs.yml`) que:

- Se dispara en cada `push` a `main`.
- Instala `mkdocs-material`.
- Corre `mkdocs gh-deploy`, que buildea el sitio y lo publica en la rama
  `gh-pages` del mismo repo.

Con esto, el flujo de trabajo queda así: **editás `.md` en `docs/` → hacés
commit → hacés push (manual, vos) → GitHub Actions buildea y publica solo**.
Nadie tiene que acordarse de correr `mkdocs build` antes de pushear.

## Pasos manuales que quedan a cargo del usuario (una sola vez)

Estos pasos requieren acceso a la configuración del repo en GitHub y no los
puede hacer Claude:

1. **Resolver la autenticación con GitHub** (no hay `gh` CLI instalado):
   configurar una clave SSH (`ssh-keygen` + agregarla en
   GitHub → Settings → SSH and GPG keys) o un Personal Access Token si se
   prefiere HTTPS.
2. **Hacer el primer push** de la rama `main` con el contenido del repo:
   ```bash
   git push -u origin main
   ```
3. Esperar a que corra el workflow (pestaña **Actions** del repo en GitHub) —
   la primera ejecución crea la rama `gh-pages` automáticamente.
4. Habilitar GitHub Pages: en el repo, ir a **Settings → Pages**, y en
   "Build and deployment" elegir:
   - **Source**: `Deploy from a branch`
   - **Branch**: `gh-pages` / `/(root)`
   - Guardar.
5. Después de unos minutos, el sitio queda disponible en
   `https://solasantiago.github.io/claude/`.
6. Cada push posterior a `main` actualiza el sitio solo, sin repetir estos
   pasos (el workflow ya queda configurado).

!!! note
    El repo es privado o público según lo hayas configurado en GitHub — para
    que GitHub Pages sea accesible sin login, el repo debe ser público (o
    tener plan que soporte Pages en repos privados).
