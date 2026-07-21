# Archivos de marca — Urbis Advisory

**Dirección elegida: A · "Trama urbana"** (decidida el 21-07-2026).

Grilla de calles + una ruta que la cruza en diagonal + un nodo ámbar en la intersección.
Lectura: ciudad y territorio (la trama), movilidad y logística (la ruta), la decisión (el nodo).

Colores oficiales en `../../MARCA_URBIS.md`: navy `#0F2A47` · salvia `#5E8C5A` (sobre oscuro `#8FBF8B`) · ámbar `#D98E3D`.

---

## Archivos

| Archivo | Uso |
|---|---|
| `urbis-isotipo.svg` | **Isotipo principal.** Fondos claros. Trama completa. |
| `urbis-isotipo-blanco.svg` | Fondos oscuros (tinta `#0A1A2E`). El cuadrado va en `#16324F` para no perderse contra el fondo. |
| `urbis-isotipo-mono.svg` | Un solo color (navy). Documentos en blanco y negro, sellos, grabados. |
| `favicon.svg` | Ícono para navegador. Mismas líneas, engrosadas para que no se emborronen. |
| `favicon-32.png` · `favicon-16.png` | Respaldo PNG. **El de 16 px usa una trama aligerada** (una calle horizontal y una vertical): la trama completa se ensucia a ese tamaño. |
| `apple-touch-icon.png` | 180 px, **sin esquinas redondeadas** — iOS aplica su propia máscara. |
| `urbis-icono-512.png` | 512 px, para redes sociales, perfiles y avatar de correo. |

## Ajuste óptico por tamaño

No es el mismo dibujo escalado: el ícono tiene **dos niveles de detalle**.

- **Grande (isotipo):** trama de 2×2 calles, líneas finas al 40% de opacidad.
- **Chico (favicon):** mismas 2×2 calles pero más gruesas y con más contraste.
- **16 px:** solo una calle horizontal y una vertical.

Esto es deliberado. Si alguien regenera los PNG, debe respetar esa distinción.

---

## Pendiente: la tipografía del wordmark

⏳ **Rodrigo va a indicar la fuente** del wordmark "urbis".

Mientras tanto, en el sitio **"urbis advisory" se renderiza como texto HTML**, no como imagen. Esto es a propósito:

- Se ve nítido en cualquier pantalla y a cualquier zoom.
- Los buscadores y los lectores de pantalla leen el nombre de la empresa.
- Cuando llegue la fuente definitiva, se cambia en **un solo lugar** (`src/input.css`, variable `--font-sans`) y se actualiza en todo el sitio.

Cuando la fuente esté confirmada, se puede generar además `urbis-logo.svg` (logotipo horizontal completo con las letras convertidas a trazos), útil para documentos y presentaciones donde no se pueda instalar la tipografía.

## Cómo regenerar los PNG

Requiere `sharp` (ya está en las dependencias de desarrollo). Se genera con un script corto de Node que rasteriza el SVG a los tamaños indicados. Pídeselo a Claude Code si hace falta rehacerlos.
