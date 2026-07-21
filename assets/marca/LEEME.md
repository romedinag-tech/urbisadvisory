# Archivos de marca

## ⚠️ Estado actual: PROVISIONALES

Los SVG que están aquí (`urbis-isotipo.svg`, `urbis-isotipo-blanco.svg`) son **marcadores de posición** hechos por Claude para que el sitio funcione. **Deben reemplazarse por los archivos definitivos** que genera Rodrigo en su herramienta de diseño.

## Qué falta entregar

Ideal: **3 archivos SVG** y yo derivo el resto.

| Archivo | Qué es |
|---|---|
| `urbis-logo.svg` | Logo completo horizontal (isotipo + "urbis advisory") |
| `urbis-isotipo.svg` | Solo el símbolo, cuadrado |
| `urbis-hero.svg` | Ilustración de portada (ciudad + tren + ruta) |

Si la herramienta solo exporta PNG, entonces con **fondo transparente** (PNG-24 con alfa):

| Archivo | Tamaño | Color |
|---|---|---|
| `urbis-logo-color.png` | ≥ 2000 px de ancho | Full color |
| `urbis-logo-blanco.png` | ≥ 2000 px | Todo blanco (fondos oscuros) |
| `urbis-logo-navy.png` | ≥ 2000 px | Monocromo navy |
| `urbis-isotipo-color.png` | 1024 × 1024 | Full color |
| `urbis-isotipo-blanco.png` | 1024 × 1024 | Blanco |
| `urbis-icono-simple.png` | 512 × 512 | **Símbolo simplificado**, legible a 16 px (favicon) |
| `urbis-hero.png` | ≥ 2000 px | Full color |

**Las dos críticas:** la versión `-blanco` (el sitio tiene secciones oscuras) y `urbis-icono-simple` (favicon y avatar).

## Cómo reemplazarlos

Deja los archivos en esta carpeta con esos nombres y avisa. Hay que actualizar las referencias en los `.html` y generar el favicon.

## Colores oficiales

Ver `../../MARCA_URBIS.md`. Resumen: navy `#0F2A47` · salvia `#5E8C5A` · ámbar `#D98E3D` · hueso `#F7F6F3` · tinta `#0A1A2E`.
