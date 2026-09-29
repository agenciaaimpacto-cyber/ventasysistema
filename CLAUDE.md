# Danny Mera — Marca Personal / Comunidad de Ventas

Contexto trasladado al migrar este sitio desde una sesión de chat de claude.ai (sin repo) a Claude Code, el 15 de septiembre de 2026.

**Sitio en vivo:** [www.dannymera.com](https://www.dannymera.com) — publicado directo desde el chat, sin quedar conectado a un repositorio de GitHub. Este proyecto lo trae a un repo real para poder seguir editándolo desde Claude Code.

**Cambio de enfoque (29 de septiembre de 2026):** la página principal (`index.html`) dejó de ser sobre "Sistemas Comerciales" y ahora es sobre **Danny como referente en ventas** — técnicas, manejo de objeciones, tono/comunicación y hábitos, con una comunidad como CTA principal (formulario de lista de espera, no un grupo ya activo — ajustar la copy si Danny confirma un canal ya abierto). El contenido original de "Sistemas Comerciales" (consultoría de detección de fugas comerciales / CRM) se movió intacto a `sistemas.html`, enlazado desde el footer del home y desde el nav de `sistemas.html` de vuelta al home. Decisión pendiente de confirmar con Danny: si `sistemas.html` debería vivir en su propio dominio/subdominio en vez de ser una página interna — por ahora es lo más simple porque no requiere comprar ni configurar nada nuevo.

**Qué es cada página:**
- `index.html` — marca personal de Danny como educador/referente en ventas. Objetivo: construir comunidad y autoridad, no vender un servicio de consultoría directamente.
- `sistemas.html` — oferta de consultoría **"Sistemas Comerciales"** (detección de fugas en el proceso comercial, armado de CRM/seguimiento/automatización), con el formulario de diagnóstico gratuito. Es un producto/servicio concreto con CTA de contratación, distinto del enfoque educativo del home.

Es un negocio distinto al de seguros (`~/DannyMeraSeguros`) y a Radar Comercial (`~/RadarComercial`), aunque las tres viven bajo el mismo paraguas de marca personal de Danny. Ver notas de portafolio de negocios en memoria (`user_business_portfolio.md` del asistente).

**Estructura técnica:** dos archivos HTML autocontenidos (CSS inline en `<style>`, JS inline en `<script>` al final de cada uno) — sin build step, sin dependencias externas salvo:
- Google Fonts (Bebas Neue, DM Sans) vía CDN.
- Formulario que postea a **Formspree** (`https://formspree.io/f/xvznbpev`, mismo endpoint en ambas páginas, diferenciado por el campo oculto `_subject`), con notificación a `agenciaaimpacto@gmail.com`. Si el formulario deja de funcionar, revisar el dashboard de Formspree antes que el código.

**Pendiente para dejarlo operativo igual que los otros proyectos (Radar Comercial / Seguros):**
1. Crear repositorio en GitHub bajo `agenciaaimpacto-cyber` (no existía ninguno para este sitio al momento de la migración — se verificó por API).
2. Confirmar acceso de escritura de la GitHub App de Claude sobre el repo nuevo (ver guía técnica en `~/DannyMeraSeguros/CLAUDE.md`, sección "Cómo se configuró Radar Comercial", punto 4) — si la instalación fue con repos específicos (no "All repositories"), hay que agregar este repo nuevo a mano en `https://github.com/settings/installations`.
3. Confirmar en Netlify (cuenta `agenciaaimpacto`) si `www.dannymera.com` ya es un sitio existente ahí (deploy manual, sin Git) — de ser así, hay que reconectarlo a este repo nuevo para que quede con deploy automático desde `main`, igual que los otros dos sitios.
4. Recordar el aviso de "operational credits" de la cuenta Netlify (ver `~/DannyMeraSeguros/CLAUDE.md`) — puede afectar si los deploys nuevos no se disparan aunque el push a GitHub sí llegue.

## Nota de idioma
Igual que los otros proyectos: español neutro/chileno estándar (tú), sin acentos/voseo argentino.
