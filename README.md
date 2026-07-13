# Raster de profundidad — Embalse Río Hondo (2001)

Generación de un raster continuo de profundidad para el embalse Río Hondo (Santiago del Estero / Tucumán, Argentina) a partir de datos batimétricos históricos relevados con ecosonda + GPS.

## Descripción

Este repositorio contiene el flujo de trabajo para convertir una nube de puntos batimétricos (relevamiento de julio de 2001) en un raster de profundidad interpolado, junto con una capa complementaria de confianza espacial que indica qué tan lejos está cada píxel del dato medido más cercano.

## Datos de origen

- **Fuente**: relevamiento batimétrico del embalse Río Hondo, julio de 2001 (ecosonda + GPS embarcado).
- **Cobertura**: ~18.000 puntos con profundidad medida, incluyendo el perímetro navegado (línea de costa al momento del relevamiento) y transectas de cruce del cuerpo de agua.
- **Cota de referencia del embalse el día del relevamiento**: 273,11 m s.n.m.
- **Sistema de coordenadas**: Gauss-Krüger Faja 3 (Argentina) — `EPSG:22183` / equivalente PROJ4 `+proj=tmerc +lat_0=-90 +lon_0=-66 +k=1 +x_0=3500000 +y_0=0 +ellps=GRS80 +units=m +no_defs`

> ⚠️ **Nota sobre el sistema de coordenadas**: se detectó que el header original de la planilla (`x, y`) no corresponde a la convención habitual IGN (Norte, Este). Tras verificación con transformación inversa de Gauss-Krüger contra la ubicación real del Dique Frontal, se confirmó que `x = Este` y `y = Norte`. Además, `EPSG:22183` puede producir resultados incorrectos (desplazamiento a coordenadas erróneas) en herramientas que respeten estrictamente el orden de ejes oficial de la definición EPSG al reproyectar contra otros CRS (p. ej. superponer capas web en Web Mercator); se recomienda usar la definición PROJ4 explícita para evitar ese problema.

## Metodología

1. **Limpieza de datos**: extracción de puntos (`x`, `y`, profundidad, cota) desde la planilla original, resolución de fórmulas de cota respecto al nivel de agua del día.
2. **Definición del perímetro**: polígono de recorte a partir de la traza del perímetro navegado, para evitar extrapolar fuera del cuerpo de agua.
3. **Interpolación espacial**: `scipy.interpolate.griddata` (método `linear`, con relleno `nearest` para huecos fuera del casco convexo de puntos) sobre una grilla regular de 30 m/píxel.
4. **Recorte**: máscara del raster interpolado al polígono del perímetro navegado (`rasterio.features.geometry_mask`).
5. **Capa de confianza**: raster complementario de distancia al punto medido más cercano (`scipy.spatial.cKDTree`), para identificar zonas con baja densidad de muestreo real (interior del embalse, entre transectas).
6. **Exportación**: GeoTIFF georreferenciado (`rasterio`).

## Salidas

| Archivo | Descripción |
|---|---|
| `rio_hondo_profundidad_2001.tif` | Raster de profundidad interpolada (metros, negativo = bajo el nivel de agua de referencia) |
| `rio_hondo_confianza_2001.tif` | Raster de distancia (metros) al punto medido más cercano |

## Limitaciones conocidas

- **Cobertura desigual**: el perímetro está densamente muestreado, pero el interior del embalse solo cuenta con un número reducido de transectas, separadas por varios kilómetros. La capa de confianza debe consultarse junto con el raster de profundidad antes de usar valores del interior del lago.
- **Vigencia del dato**: el relevamiento es de 2001. La morfología del lecho puede haber cambiado por sedimentación; no representa necesariamente la batimetría actual.
- **Artefactos de interpolación lineal**: el método `linear` de `griddata` genera facetas/triangulaciones visibles en zonas de baja densidad de puntos; es un efecto esperable de la técnica, no un error de datos.

## Requisitos

```
pandas
numpy
scipy
shapely
rasterio
matplotlib
```

## Autoría

Procesamiento y análisis: [tu nombre/usuario]
Datos originales: relevamiento batimétrico Río Hondo, julio 2001
