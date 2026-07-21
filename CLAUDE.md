# CLAUDE.md — Sitio web de Urbis Advisory

> Este archivo lo lee Claude Code automáticamente al iniciar cada sesión en este repositorio.
> Contiene las reglas y el contexto que deben mantenerse constantes en el tiempo. Actualízalo cuando algo cambie.

## Qué es este proyecto

Sitio web corporativo de **Urbis Advisory** (marca comercial de **Medina Consultoría SpA**, RUT 78.398.141-6), consultora chilena en desarrollo urbano, movilidad, logística y analítica de datos, con base en Concepción.

- **Dominio de producción:** urbisadvisory.com
- **Objetivo del sitio:** presentar los servicios y, sobre todo, **poner en valor las 4 plataformas de analítica propias** (el principal diferenciador). Captar contacto de clientes: GORE, municipios, inmobiliarias, gremios, operadores logísticos.
- **Tono:** técnico, sobrio, confiable, orientado a decisiones e inversión pública/privada. Nada de marketing exagerado.

## Identidad visual (mantener consistente)

> ⚠️ **Paleta actualizada el 21-07-2026** (Opción A: Navy + Salvia). Reemplaza a la anterior navy/teal del GORE.
> **Fuente de verdad completa: `../MARCA_URBIS.md`** — leerlo antes de tocar colores.

**Paleta de marca** (web, logo, títulos, botones):
- Tinta / fondos oscuros: `#0A1A2E`
- Navy primario: `#0F2A47`
- Secundario verde salvia: `#5E8C5A` (sobre oscuro se aclara a `#8FBF8B`)
- Acento ámbar: `#D98E3D` — **solo CTAs**, menos del ~10% de la superficie
- Fondo claro (hueso): `#F7F6F3` · Panel: `#EFEDE8` · Línea: `#E0DDD6`
- Texto: `#14283F` · Texto suave: `#5C6B73` · Sobre oscuro: `#B7C4D4`

**Paleta de datos** (solo en gráficos y secciones dashboard): teal `#17A398`, verde `#6FA96B`, ámbar `#D98E3D`, azul `#3E86C4`, violeta `#8A6FB5`, arcilla `#C96F4F`. Rampas secuencial y divergente en `MARCA_URBIS.md`.

**Reglas:** un solo acento · nada de rojo saturado ni la tríada rojo+blanco+azul (evitar lectura partidaria) · tonos desaturados en la marca, color vivo solo en los datos · las secciones oscuras son bloques puntuales, el inicio va en claro.

Tipografía: sans-serif del sistema (Arial/Helvetica/Inter). Titulares en peso bold, buen contraste de tamaño. Layout limpio, mucho espacio en blanco. **Evitar** rayas/subrayados decorativos bajo títulos y barras de color de relleno (se ven "auto-generados").

Marca: mostrar **"Urbis"** con fuerza y **"Advisory"** en menor tamaño. Nombre de fantasía correcto: **Urbis Advisory** (ojo con la ortografía: a-d-v-i-s-o-r-y).

## Las 3 plataformas que se muestran en el sitio

1. **Ciudades y tendencias de Chile** — SII (manzana) + Censo + CASEN, 345 comunas → https://romedinag-tech.github.io/ciudades_y_tendencias_de_Chile/
2. **Comercio exterior de Chile** — DUS/DIN de Aduanas por punto de transferencia → https://romedinag-tech.github.io/comercio-exterior-chile/
3. **EOD Chile** — Encuestas Origen-Destino en un repositorio + modelo calibrado → https://romedinag-tech.github.io/EOD-Chile/

> ⛔ **El dashboard de Transporte público Gran Concepción (GPS en vivo) NO va en el sitio.**
> Decisión de Rodrigo del 21-07-2026. La plataforma existe y sigue siendo un activo del negocio
> (ver `0 Contexto Claude/CONTEXTO.md`), pero **no se publica ni se enlaza desde la web**. No volver a agregarla.
> Por lo mismo, la cifra "302 M registros GPS" se retiró de la franja de cifras del inicio: su respaldo público era ese tablero.

Las capturas de las plataformas viven en `assets/dashboards/`. Se pueden regenerar en cualquier momento
navegando a cada URL y capturando la pantalla (se hicieron con las herramientas de Chrome DevTools).

## Líneas de servicio a comunicar

- Desarrollo urbano y planificación territorial (planes reguladores, PLADECO, PROT, PIIMEP)
- Movilidad y transporte (**IMIV**: elaboración, revisión y rescate de informes; modelación; diagnóstico de transporte público)
- Logística y comercio exterior (análisis de carga por puerto, hinterland)
- Fotografía aérea y levantamientos (aerofotogrametría, topografía, teledetección)
- Analítica de big data aplicada a la decisión (transversal)
- Asesoría comercial inmobiliaria (localización, mercado del suelo)

> La **línea electoral** NO va en este sitio: tiene marca y web propias aparte (decisión tomada para no mezclar el posicionamiento técnico con lo político).

## Datos de contacto

- Correo: **rmedina@urbisadvisory.com** (y contacto@urbisadvisory.com cuando se cree el alias)
- Responsable: Rodrigo Medina González — Ingeniero Civil, ex Director Nacional de Planificación de SECTRA (MTT)
- Ciudad: Concepción, Región del Biobío, Chile

## Reglas técnicas del proyecto

- Sitio **estático multipágina** con **Tailwind CSS v4** (decisión del 21-07-2026, reemplaza al CSS vanilla).
  - El tema de marca vive en `src/input.css` dentro del bloque `@theme`. **Los colores se cambian ahí, no en los HTML.**
  - Compilar con `npm run build` (o `npm run dev` para recompilar al vuelo). Salida: `dist/styles.css`.
  - En producción compila solo GitHub Actions (`.github/workflows/deploy.yml`); Rodrigo no necesita correr npm.
  - Componentes de referencia: **HyperUI** (Tailwind, MIT). Se usan como esqueleto y se re-estilizan con la paleta propia — nunca pegar un bloque tal cual, se nota plantilla.
  - **No** se usa React ni 21st.dev: estética efectista (shaders, metal líquido) incompatible con el posicionamiento institucional, y el stack sería sobredimensionado.
- Páginas: `index.html` · `quienes-somos.html` · `que-hacemos.html` · `productos.html` · `contacto.html`.
  - El header, el rail izquierdo y el footer están **duplicados en cada página**. Si se cambia uno, cambiarlos en las cinco.
- Estructura de layout: barra superior + **rail izquierdo fijo** (contacto + los 4 dashboards) junto al contenido.
- **Responsive** (móvil primero). Probar en anchos chicos.
- Accesibilidad: buen contraste, textos alt en imágenes, navegación por teclado.
- SEO básico: `<title>`, meta description, Open Graph, favicon, `sitemap.xml`.
- **No romper el correo:** el dominio urbisadvisory.com ya tiene MX (Google), SPF, DKIM y DMARC configurados en Squarespace. **Nunca tocar esos registros** al configurar el hosting del sitio; solo se ajustan los registros del sitio web (A/CNAME) según el proveedor de hosting.

## Estado / decisiones

- **Despliegue: GitHub Pages con build automático en GitHub Actions.** Falta crear el repo y hacer el primer push.
- Dominio registrado en Squarespace; DNS administrado ahí. `CNAME` ya incluido en el repo.
- El sitio v1 (one-pager en CSS vanilla) quedó archivado en `_v1-anterior/`, fuera de publicación.

### Pendientes conocidos
- [ ] **Logo definitivo.** Los SVG en `assets/marca/` son provisionales — ver `assets/marca/LEEME.md`.
- [ ] **Tipografía**: el tema declara Inter pero no se carga webfont (cae a la fuente del sistema). Definir al confirmar la fuente del wordmark.
- [ ] **Favicon** derivado del ícono simplificado, cuando llegue.
- [ ] **Formulario de contacto**: hoy la página usa correo y teléfono directos. Para un formulario real hace falta un servicio externo (ej. Formspree), porque el sitio es estático y no tiene backend.
- [ ] Capturas reales de los 4 dashboards para la página de productos.
- [ ] Ilustración de portada, si se decide sumarla al video.
