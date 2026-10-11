# Baltic Transline — Carga de documentos

Sitio estático para que postulantes suban su documentación (pasaporte, identidad, licencias, antecedentes, apostillado, certificado médico) y descarguen los formularios de la empresa.

## Tecnologías

- HTML/CSS estático (sin framework)
- Netlify Forms con subida de archivos (`multipart/form-data`)
- Notificaciones por email de Netlify Forms

## Estructura

- `public/index.html` — página de carga con formulario Netlify Form
- `public/gracias.html` — página de agradecimiento tras el envío
- `public/documentos/` — PDFs descargables para el postulante
- `netlify.toml` — configuración de build (publish: `public`)

## Cómo correr localmente

```bash
netlify dev --port 8889
```

El formulario requiere deploy en Netlify para funcionar (Netlify Forms se activa en el deploy).

## Límites

- Tamaño máximo de envío: 8 MB por request
- Un archivo por campo (Netlify Forms no soporta `multiple`)
- Notificaciones email: configurar en Project configuration > Forms > Notifications