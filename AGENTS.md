# Klaus — guía para agentes

> Guía única del repo: la leen Claude Code (vía `CLAUDE.md`), Codex, OpenCode y otros agentes · Nivel P1 · Verificado contra el código el 24-oct-2026.
> Leé esto entero; las trampas están en `LECCIONES.md`. Castellano rioplatense.
> ⚠️ **Este repo es GitHub Pages: sus `.md` (incluido este) pueden quedar servidos en público.** Nada interno acá: sin credenciales, teléfonos de socios ni wikilinks `[[…]]` del vault (no sirven en un repo).

## Qué es

Landing estática de la marca **Klaus** (sociedad). Sitio de una sola página en HTML/CSS/JS puro, sin dependencias ni backend. Publicado en GitHub Pages con dominio propio en Hostinger.

Secciones: hero · manifiesto · servicios · **portfolio (6 proyectos públicos: Hermes, Fidelio Web, Columen, Mascotitas, Creador de Mensajes, De puño y letra)** · proceso · equipo · CTA. Estética Apple minimal: negro/plateado, Hanken Grotesk, un elemento sutil de luz neón y riel de progreso vertical.

## Estado hoy

- **Deployado y estable**: v6.1 (commit `75b358e`, 10-sep-2026). Último cambio: riel de progreso y mail `bernabe05rodriguez@gmail.com`. Sin trabajo pendiente salvo cambios al portfolio.
- **Dominio**: klaus-software.online (Hostinger). Apunta a GitHub Pages.
- **Repo**: `bernabe05rodriguez-stack/Klaus` (GitHub). Pages: https://bernabe05rodriguez-stack.github.io/Klaus/
- **Hosting**: GitHub Pages (CNAME `klaus-software.online` en el repo). Un `git push` a `master` publica en ~45 segundos.
- El repo también trae `Dockerfile` (nginx:alpine que copia todo a `/usr/share/nginx/html`) y `.dockerignore`, agregados el 14-oct para EasyPanel: existe el servicio `redhawk/klaus` (rama `master`, prendido, sin despliegue automático), pero **el dominio lo sirve GitHub Pages** (verificado el 24-oct: `klaus-software.online` resuelve a las IP de GitHub y responde `server: GitHub.com`). El servicio de EasyPanel es una copia que no atiende el dominio.
- Rama `master` (no `main`).

## Stack y mapa

HTML/CSS/JS estático, cero dependencias. Single page.

| Qué | Dónde |
|---|---|
| Página completa, estilos, animaciones, JSON-LD (SEO y contacto en `<head>`) | `index.html` (todo en un archivo, en la raíz) |
| Marca: 512 px (watermark del CTA, JSON-LD), nav y footer | `logo-mark.png` · `logo-nav.png` · `logo-footer.png` |
| Favicons | `favicon.png` · `favicon-48.png` · `favicon-96.png` · `apple-touch-icon.png` |
| Imagen para compartir (1200×630) | `og-image.jpg` |
| Dominio custom de Pages | `CNAME` |
| SEO | `robots.txt` · `sitemap.xml` |
| Fuente Hanken Grotesk | Google Fonts (`<link>` en `index.html`; no hay fuentes locales) |
| Servir con nginx | `Dockerfile` · `.dockerignore` |

Efectos scroll-driven (hero sticky, manifiesto palabra por palabra, luz de neón entre waypoints, riel de progreso de 1 px) con `IntersectionObserver` + `requestAnimationFrame`; respetan `prefers-reduced-motion`.

## Reglas duras

1. **`index.html` es CRLF (Windows)**: al editar por script, normalizar saltos de línea después; si queda mezclado CRLF + LF, el siguiente commit de Berna choca (`LECCIONES.md`).
2. **Hosting en GitHub Pages**: no mezclar con EasyPanel ni doble hosting. Pages es la fuente única (Columen y Creador-Mensajes tuvieron formularios rotos por doble hosting; acá no aplica porque no hay backend).
3. **Fondo negro liso**: Berna rechazó explícitamente (10-sep) fondos dinámicos (grilla, números, tokens, código). Si se propone un elemento visual nuevo, que sea **uno solo**, sutil, no saturado.
4. **Portfolio siempre público**: los 6 links en el portfolio deben apuntar a proyectos públicos (Hermes, Fidelio Web, Columen, Mascotitas, Creador-Mensajes, De puño y letra). Sin links a repos privados ni a borradores.
5. **Mail de contacto único**: `bernabe05rodriguez@gmail.com` (en CTA, JSON-LD, atributos `href="mailto:`). No cambiar sin confirmación de Berna.
6. **Los socios son Franco, Bautista y Bernabé**: datos en la ficha del vault (`proyectos/Klaus.md`). Si alguien cambia de contacto, actualizar ahí; aquí no va.
7. **Sin credenciales ni datos privados**: GitHub Pages publica TODO el repo, `.md` incluidos. Nada de secretos, teléfonos de socios ni datos internos (los números de los socios viven solo en la ficha del vault).

## Probar

```bash
python3 -m http.server -d . 8000      # http://localhost:8000
```
Mirar escritorio y celular, y el riel/luz de neón al scrollear. Tras publicar, verificar https://klaus-software.online.

## Desplegar

`git push origin master` con git de Windows (es CRLF); Pages publica en ~45 segundos. Después chequear https://klaus-software.online.

## Si vas a tocar X, leé Y

| Si vas a tocar… | Leé |
|---|---|
| Portfolio (links de proyectos) | Ficha `proyectos/Klaus.md` del vault |
| Cualquier cosa: trampas ya pagadas | `LECCIONES.md` |
| Estilos, animaciones, layout | `index.html` (está todo en una página) |
| Contacto, JSON-LD, SEO | `index.html`, sección `<head>` |
| Historial de cambios, decisiones de diseño | Ficha `Klaus-historial.md` del vault |

## Cómo se documenta acá

- `AGENTS.md` (esto) es la guía; `CLAUDE.md` solo la importa. Sin `docs/` (proyecto chico). `LECCIONES.md`: trampas. Sin `BACKLOG.md` (nada abierto).
- Un dato que envejece (última versión, URLs) va UNA vez, en «Estado hoy». Lo obsoleto se borra (git guarda la historia).
- Ficha, decisiones de diseño, historial de cambios: vault `G:\Mi unidad\Trabajo\cerebro\` (WSL `/mnt/g/Mi unidad/Trabajo/cerebro/`), archivos `proyectos/Klaus.md` y `Klaus-historial.md`. Reglas para todos los agentes: `_compartido-agentes.md` del vault.
- Git con el de Windows (`powershell.exe -Command "git -C '<ruta>' ..."` desde WSL); `git pull` antes de empezar. Rama `master`, no `main`.
