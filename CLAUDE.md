# Danny Mera — Marca Personal (Ventas + Sistemas Comerciales)

Contexto trasladado al migrar este sitio desde una sesión de chat de claude.ai (sin repo) a Claude Code, el 15 de septiembre de 2026.

**Este repo contiene DOS sitios independientes, cada uno en su propia carpeta:**
- `ventas/` → **dannymera.com** (dominio propio oficial). Marca personal de Danny como educador/referente en ventas — técnicas, manejo de objeciones, tono/comunicación, hábitos, con una comunidad como CTA principal (formulario de lista de espera, no un grupo ya activo — ajustar la copy si Danny confirma un canal ya abierto).
- `sistemas/` → **dannymerasistemas** (por ahora solo un subdominio gratis de Netlify, sin dominio propio — idealmente `dannymerasistemas.netlify.app`). Oferta de consultoría "Sistemas Comerciales": detección de fugas en el proceso comercial, armado de CRM/seguimiento/automatización, con formulario de diagnóstico gratuito.

**Por qué un solo repo con dos sitios (decisión del 29 de septiembre de 2026):** Netlify necesita un sitio por dominio si el contenido es distinto (un sitio no puede mostrar cosas diferentes según el dominio que lo visite). Pero eso no obliga a tener dos repos de GitHub — un solo repo puede alimentar dos sitios de Netlify si cada uno se configura con una **"base directory" / "publish directory" distinta**:
- Sitio Netlify de `dannymera.com` → base directory: `ventas`
- Sitio Netlify de `dannymerasistemas` → base directory: `sistemas`

Así un solo `git push` puede actualizar cualquiera de los dos sitios (Netlify solo redeploya el que tenga cambios en su carpeta), y solo hay que mantener un repo, no dos. (Se probó primero con dos repos separados — `~/DannyMeraSistemas` — pero se consolidó de vuelta a uno para simplificar, ya que "sistemas" por ahora es solo un subdominio gratis, sin necesidad real de infraestructura independiente todavía.)

Cada `index.html` es autocontenido (CSS inline en `<style>`, JS inline en `<script>` al final) — sin build step, sin dependencias externas salvo:
- Google Fonts (Bebas Neue, DM Sans) vía CDN, en ambos.
- Formulario que postea a **Formspree** (`https://formspree.io/f/xvznbpev`, mismo endpoint en ambos sitios, diferenciado por el campo oculto `_subject`), con notificación a `agenciaaimpacto@gmail.com`. Si un formulario deja de funcionar, revisar el dashboard de Formspree antes que el código.

Cross-links entre los dos sitios son URLs absolutas (no relativas), porque viven en dominios distintos:
- `ventas/index.html` → footer enlaza a `https://dannymerasistemas.netlify.app`.
- `sistemas/index.html` → nav-logo enlaza a `https://www.dannymera.com`.
Si el subdominio real de Netlify para "sistemas" queda con otro nombre (por disponibilidad), hay que corregir el link del footer en `ventas/index.html`.

Es un negocio distinto al de seguros (`~/DannyMeraSeguros`) y a Radar Comercial (`~/RadarComercial`), aunque viven bajo el mismo paraguas de marca personal de Danny. Ver notas de portafolio de negocios en memoria (`user_business_portfolio.md` del asistente).

**Pendiente para dejarlo operativo igual que los otros proyectos:**
1. Crear repositorio en GitHub bajo `agenciaaimpacto-cyber` (no existía ninguno para este sitio al momento de la migración — se verificó por API).
2. Confirmar acceso de escritura de la GitHub App de Claude sobre el repo nuevo (ver guía técnica en `~/DannyMeraSeguros/CLAUDE.md`, sección "Cómo se configuró Radar Comercial", punto 4) — si la instalación fue con repos específicos (no "All repositories"), hay que agregar este repo nuevo a mano en `https://github.com/settings/installations`.
3. En Netlify (cuenta `agenciaaimpacto`): reconectar el sitio que ya sirve `www.dannymera.com` a este repo, con base directory `ventas`.
4. En Netlify: crear un sitio nuevo para "sistemas", conectado a este mismo repo, con base directory `sistemas`, sin dominio propio (solo el subdominio que asigne Netlify) — confirmar el nombre final y corregir el link del footer en `ventas/index.html` si no es `dannymerasistemas.netlify.app`.
5. Recordar el aviso de "operational credits" de la cuenta Netlify (ver `~/DannyMeraSeguros/CLAUDE.md`) — puede afectar si los deploys nuevos no se disparan aunque el push a GitHub sí llegue.

## Nota de idioma
Igual que los otros proyectos: español neutro/chileno estándar (tú), sin acentos/voseo argentino.
