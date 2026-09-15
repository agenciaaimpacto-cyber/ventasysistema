# Danny Mera — Marca Personal / Sistemas Comerciales

Contexto trasladado al migrar este sitio desde una sesión de chat de claude.ai (sin repo) a Claude Code, el 15 de septiembre de 2026.

**Sitio en vivo:** [www.dannymera.com](https://www.dannymera.com) — publicado directo desde el chat, sin quedar conectado a un repositorio de GitHub. Este proyecto lo trae a un repo real para poder seguir editándolo desde Claude Code.

**Qué es este sitio:** landing page de una sola página para la marca personal de Danny y su oferta de consultoría de **"Sistemas Comerciales"** — detección de fugas en el proceso comercial (leads que llegan pero no se convierten) y armado de sistema de seguimiento/CRM/automatización. Es un negocio distinto al de seguros (`~/DannyMeraSeguros`) y a Radar Comercial (`~/RadarComercial`), aunque las tres viven bajo el mismo paraguas de marca personal de Danny. Ver notas de portafolio de negocios en memoria (`user_business_portfolio.md` del asistente).

**Estructura técnica:** un solo archivo `index.html` autocontenido (CSS inline en `<style>`, JS inline en `<script>` al final) — sin build step, sin dependencias externas salvo:
- Google Fonts (Bebas Neue, DM Sans) vía CDN.
- Formulario de diagnóstico gratuito que postea a **Formspree** (`https://formspree.io/f/xvznbpev`), con notificación a `agenciaaimpacto@gmail.com`. Si el formulario deja de funcionar, revisar el dashboard de Formspree antes que el código.

**Pendiente para dejarlo operativo igual que los otros proyectos (Radar Comercial / Seguros):**
1. Crear repositorio en GitHub bajo `agenciaaimpacto-cyber` (no existía ninguno para este sitio al momento de la migración — se verificó por API).
2. Confirmar acceso de escritura de la GitHub App de Claude sobre el repo nuevo (ver guía técnica en `~/DannyMeraSeguros/CLAUDE.md`, sección "Cómo se configuró Radar Comercial", punto 4) — si la instalación fue con repos específicos (no "All repositories"), hay que agregar este repo nuevo a mano en `https://github.com/settings/installations`.
3. Confirmar en Netlify (cuenta `agenciaaimpacto`) si `www.dannymera.com` ya es un sitio existente ahí (deploy manual, sin Git) — de ser así, hay que reconectarlo a este repo nuevo para que quede con deploy automático desde `main`, igual que los otros dos sitios.
4. Recordar el aviso de "operational credits" de la cuenta Netlify (ver `~/DannyMeraSeguros/CLAUDE.md`) — puede afectar si los deploys nuevos no se disparan aunque el push a GitHub sí llegue.

## Nota de idioma
Igual que los otros proyectos: español neutro/chileno estándar (tú), sin acentos/voseo argentino.
