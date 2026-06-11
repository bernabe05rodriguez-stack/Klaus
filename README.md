# Klaus — Landing

Sitio institucional de **Klaus Software** · [klaus-software.online](https://klaus-software.online)

## Stack

- Un solo `index.html` — HTML/CSS/JS vanilla, sin dependencias ni build.
- Tipografía: Hanken Grotesk (Google Fonts). Paleta: negro + monocromo plateado.
- Efectos scroll-driven (hero sticky, manifiesto palabra por palabra, contadores) con `IntersectionObserver` + `requestAnimationFrame`. Respeta `prefers-reduced-motion`.

## Deploy

GitHub Pages desde `master`. Cada push a `master` publica automáticamente en el dominio (CNAME incluido en el repo).

## Archivos

| Archivo | Uso |
|---|---|
| `index.html` | Todo el sitio |
| `logo-mark.png` | Marca 512px (watermark CTA, JSON-LD) |
| `logo-nav.png` / `logo-footer.png` | Marca chica para nav y footer |
| `favicon.png` | Favicon (marca blanca sobre negro redondeado) |
| `og-image.jpg` | Imagen para compartir (1200×630) |
| `CNAME` | Dominio custom de GitHub Pages |
