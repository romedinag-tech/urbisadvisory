# Archivos de marca — Urbis Advisory

**Dirección elegida: A · "Trama urbana"** (decidida el 21-07-2026).

Grilla de calles + una ruta que la cruza en diagonal + un nodo ámbar en la intersección.
Lectura: ciudad y territorio (la trama), movilidad y logística (la ruta), la decisión (el nodo).

Colores oficiales en `../../MARCA_URBIS.md`: navy `#0F2A47` · salvia `#5E8C5A` (sobre oscuro `#8FBF8B`) · ámbar `#D98E3D`.

---

## Archivos

| Archivo | Uso |
|---|---|
| `urbis-logo.svg` | **Logotipo horizontal completo** (isotipo + "urbis advisory"). Para documentos, presentaciones, membretes y firmas de correo. |
| `urbis-logo-blanco.svg` | El mismo, para fondos oscuros. |
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

## Tipografía

✅ **Outfit** para el wordmark y los titulares · **Inter** para el cuerpo de texto.
Ambas libres (SIL OFL) y auto-alojadas en `../fonts/`. Detalle en `../../MARCA_URBIS.md`.

### Por qué hay dos formas del wordmark

| Dónde | Cómo | Por qué |
|---|---|---|
| **En el sitio web** | Texto HTML con la fuente Outfit | Se ve nítido a cualquier zoom, y buscadores y lectores de pantalla leen el nombre de la empresa. |
| **En `urbis-logo.svg`** | Letras convertidas a **trazos** | No depende de tener Outfit instalada: se ve igual en cualquier computador, Word, PowerPoint o imprenta. |

Las dos deben verse idénticas. Si algún día se cambia la tipografía, hay que regenerar el SVG.

### Cómo se generó el logotipo

Con `fontTools`, extrayendo los contornos de `../fonts/outfit.woff2` (peso 700 para "urbis", 600 para "advisory").
**"ADVISORY" va justificada al ancho exacto de "urbis"** — el tracking se calcula, no se elige a ojo. Si se regenera, mantener esa regla.

## Cómo regenerar los PNG

Requiere `sharp` (ya está en las dependencias de desarrollo). Se genera con un script corto de Node que rasteriza el SVG a los tamaños indicados. Pídeselo a Claude Code si hace falta rehacerlos.
