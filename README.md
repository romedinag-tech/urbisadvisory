# urbisadvisory-web

Sitio web de **Urbis Advisory** (Medina Consultoría SpA). Sitio estático multipágina con **Tailwind CSS v4**, pensado para mantenerse con Claude Code.

## Estructura

```
index.html            Inicio (hero con video, cifras, servicios, plataformas)
quienes-somos.html    Perfil, ámbitos de experiencia, enfoque, datos de la empresa
que-hacemos.html      Las 6 líneas de servicio en detalle
productos.html        Las 4 plataformas de analítica
contacto.html         Contacto y datos de la empresa

src/input.css         ⭐ Tema de marca (bloque @theme). Los colores se cambian AQUÍ.
dist/styles.css       CSS compilado (generado, no editar a mano)
assets/marca/         Logo (PROVISIONAL — ver LEEME.md)
assets/video/         Video del hero comprimido + posters
_v1-anterior/         Sitio v1 archivado, no se publica
```

## Ver el sitio localmente

```bash
npm install          # solo la primera vez
npm run build        # compila dist/styles.css
```

Luego levanta un servidor (necesario para que carguen video y rutas):

```bash
python -m http.server 8899
# abrir http://127.0.0.1:8899
```

Para trabajar con recompilación automática mientras editas:

```bash
npm run dev
```

> ⚠️ Abrir `index.html` con doble clic **no** funciona bien: el navegador bloquea parte de los assets con `file://`. Usa el servidor local.

## Cambiar colores

**No** toques los HTML. Edita el bloque `@theme` de `src/input.css` y recompila. La fuente de verdad de la paleta es `../MARCA_URBIS.md`.

## Publicar en urbisadvisory.com

El repositorio ya trae `.github/workflows/deploy.yml`: **el CSS se compila solo en GitHub Actions** en cada push a `main`. No necesitas correr npm para publicar.

**Pasos, una sola vez:**

1. Crear el repo y subir:
   ```bash
   git init
   git add .
   git commit -m "Sitio Urbis Advisory v2"
   git branch -M main
   git remote add origin https://github.com/romedinag-tech/urbisadvisory-web.git
   git push -u origin main
   ```
2. En GitHub → **Settings → Pages → Source: GitHub Actions**.
3. En **Squarespace (DNS)**, apuntar el dominio a GitHub Pages:
   - Registros **A** de `@`: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - **CNAME** `www` → `romedinag-tech.github.io`
4. En GitHub Pages, activar **Enforce HTTPS**.

> 🚨 **No tocar los registros MX ni los TXT de SPF/DKIM/DMARC.** Esos son del correo de `urbisadvisory.com` y romperlos deja a Rodrigo sin correo. Solo se modifican los A/CNAME del sitio.

## Video del hero

- `hero-desktop.mp4` (3,5 MB) — aéreo nocturno, comprimido desde 4K.
- `hero-mobile.mp4` (1,5 MB) — vertical con estelas de tráfico.
- Ambos van muteados, en loop y con imagen poster de respaldo.
- Se **ocultan** con `prefers-reduced-motion` (queda el poster).
- Origen: Pexels/Pixabay, licencia libre para uso comercial sin atribución.
- ⛔ Los archivos `istockphoto-*_adpp_is.mp4` de la carpeta de origen son *comps* con marca de agua: **no se pueden publicar**.

## Pendientes

- [ ] Reemplazar el logo provisional (ver `assets/marca/LEEME.md`).
- [ ] Favicon definitivo desde el ícono simplificado.
- [ ] Definir tipografía (hoy cae a la fuente del sistema).
- [ ] Formulario de contacto con servicio externo (Formspree u otro), si se quiere además del correo directo.
- [ ] Capturas reales de los 4 dashboards en `productos.html`.
