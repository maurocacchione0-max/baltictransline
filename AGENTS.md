# AGENTS.md

## Arquitectura

Sitio estático puro (sin framework ni SSR) servido desde `public/`. `netlify.toml` apunta `publish` a `public/`. El build es trivial: no hay paso de compilación.

## Claves

- `public/index.html` contiene un Netlify Form (`carga-documentos`) con `data-netlify="true"`, `enctype="multipart/form-data"`, honeypot `bot-field` y acción `/gracias`.
- Netlify detecta el form en build-time porque el HTML es estático — no hace falta skeleton file (eso es sólo para apps SSR/SPA).
- `public/documentos/` tiene los PDFs descargables; los nombres de archivo tienen espacios y acentos — servir con URLs encodeadas (`%20`, `%C3%AD`).
- Subida de archivos: límite Netlify Forms 8 MB/request, 1 archivo por input. No usar `multiple` en inputs file.

## Convenciones

- Contenido y UI en español (público: postulantes de Baltic Transline).
- Sin build step: editar HTML directamente en `public/`.
- `gracias.html` es la action del form — si se cambia el nombre, actualizar `action="/gracias"` en `index.html`.

## Feature flags / activación

- `.netlify/features/netlify-forms` (marcador creado por el script enable del skill) activa Netlify Forms en el deploy.