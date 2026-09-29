# Danny Mera — Marca Personal (Ventas + Sistemas Comerciales)

Contexto trasladado al migrar este sitio desde una sesión de chat de claude.ai (sin repo) a Claude Code, el 15 de septiembre de 2026.

**Este repo contiene DOS sitios independientes, cada uno en su propia carpeta:**
- `ventas/` → **dannymera.com** (dominio propio oficial). Marca personal de Danny como educador/referente en ventas — técnicas, manejo de objeciones, tono/comunicación, hábitos, con una comunidad como CTA principal (formulario de lista de espera, no un grupo ya activo — ajustar la copy si Danny confirma un canal ya abierto).
- `sistemas/` → **dannymerasistemas** (por ahora solo un subdominio gratis de Netlify, sin dominio propio: **`dannymera-sistemas.netlify.app`**, confirmado en el dashboard de Netlify el 29 de septiembre). Oferta de consultoría "Sistemas Comerciales": detección de fugas en el proceso comercial, armado de CRM/seguimiento/automatización, con formulario de diagnóstico gratuito.

**Por qué un solo repo con dos sitios (decisión del 29 de septiembre de 2026):** Netlify necesita un sitio por dominio si el contenido es distinto (un sitio no puede mostrar cosas diferentes según el dominio que lo visite). Pero eso no obliga a tener dos repos de GitHub — un solo repo puede alimentar dos sitios de Netlify si cada uno se configura con una **"base directory" / "publish directory" distinta**:
- Sitio Netlify de `dannymera.com` → base directory: `ventas`
- Sitio Netlify de `dannymerasistemas` → base directory: `sistemas`

Así un solo `git push` puede actualizar cualquiera de los dos sitios (Netlify solo redeploya el que tenga cambios en su carpeta), y solo hay que mantener un repo, no dos. (Se probó primero con dos repos separados — `~/DannyMeraSistemas` — pero se consolidó de vuelta a uno para simplificar, ya que "sistemas" por ahora es solo un subdominio gratis, sin necesidad real de infraestructura independiente todavía.)

Cada `index.html` es autocontenido (CSS inline en `<style>`, JS inline en `<script>` al final) — sin build step, sin dependencias externas salvo:
- Google Fonts (Bebas Neue, DM Sans) vía CDN, en ambos.
- Formulario que postea a **Formspree** (`https://formspree.io/f/xvznbpev`, mismo endpoint en ambos sitios, diferenciado por el campo oculto `_subject`), con notificación a `agenciaaimpacto@gmail.com`. Si un formulario deja de funcionar, revisar el dashboard de Formspree antes que el código.

Cross-links entre los dos sitios son URLs absolutas (no relativas), porque viven en dominios distintos:
- `ventas/index.html` → footer enlaza a `https://dannymera-sistemas.netlify.app`.
- `sistemas/index.html` → nav-logo enlaza a `https://www.dannymera.com`.

Es un negocio distinto al de seguros (`~/DannyMeraSeguros`) y a Radar Comercial (`~/RadarComercial`), aunque viven bajo el mismo paraguas de marca personal de Danny. Ver notas de portafolio de negocios en memoria (`user_business_portfolio.md` del asistente).

**Estado: completamente operativo desde el 29 de septiembre de 2026.** Repo en GitHub: [agenciaaimpacto-cyber/ventasysistema](https://github.com/agenciaaimpacto-cyber/ventasysistema) (un solo repo para los dos sitios). Configuración final en Netlify:
- Proyecto **`dannymera-ventas`** (renombrado por Netlify a "dannymera.com" al agregar el dominio) → conectado a este repo, base/publish directory `ventas`, dominio primary `dannymera.com` + alias `www.dannymera.com` (redirige al primary), HTTPS forzado, certificado Let's Encrypt activo.
- Proyecto **`dannymera-sistemas`** (el que ya existía, antes deployado manualmente vía Netlify Drop sin repo) → reconectado a este mismo repo, base/publish directory `sistemas`, sin dominio propio, accesible solo en `dannymera-sistemas.netlify.app`.

Ambos se redeployan automáticamente con cada `git push` a `main` (Netlify solo reconstruye el sitio cuya carpeta cambió). Verificado en vivo el 29 de septiembre: `www.dannymera.com` sirve la página de ventas, y el link del footer "Conoce Sistemas Comerciales →" lleva correctamente a `dannymera-sistemas.netlify.app`.

**Nota de configuración importante para el futuro:** en el formulario de "Link repository" / "Add new project" de Netlify, el campo "Publish directory" se muestra como un prefijo fijo (el valor de "Base directory" + `/`) seguido de un campo editable para una subcarpeta adicional — si el sitio está directamente en la raíz de esa carpeta (como acá, sin subcarpeta extra), hay que dejar esa parte vacía, no reescribir el nombre de la carpeta ahí (eso duplicaría la ruta, ej. `sistemas/sistemas`).

## Nota de idioma
Igual que los otros proyectos: español neutro/chileno estándar (tú), sin acentos/voseo argentino.
