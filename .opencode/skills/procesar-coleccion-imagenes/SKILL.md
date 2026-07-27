---
name: procesar-coleccion-imagenes
description: >-
  Use when the user asks to process, optimize, or convert images for a new
  CROMINUS collection. Triggered by keywords like "optimizar imagenes",
  "nueva coleccion de imagenes", "procesar coleccion", "convertir a webp",
  or when new PNG/JPG images are added to a collection folder.
  Do NOT use for generating collection JSON files.
---

# Procesar Imágenes de Colección CROMINUS

Workflow para optimizar, renombrar y generar thumbnails de una colección de cromos.

## Flujo de trabajo

### Paso 1: Identificar la colección
- Buscar carpetas en `collections/` que contengan imágenes PNG/JPG sin procesar
- Si solo hay una, presentarla al usuario para confirmar
- Si hay varias, preguntar cuál procesar
- Contar archivos y comprobar dimensiones

### Paso 2: Recopilar datos del usuario
Preguntar siempre (no asumir):

| Dato | Ejemplo | Obligatorio |
|---|---|---|
| Código referencia | `cro-pk-mcc` | sí |
| Dimensiones originales | 660x920 | sí (auto-detectar y confirmar) |
| Padding números | 3 dígitos (001) | sí (confirmar) |

### Paso 3: Confirmar parámetros de salida
Preguntar al usuario:

| Parámetro | Opciones | Default si no responde |
|---|---|---|
| Calidad WebP | 75-95 | 85 |
| Altura thumbnails | px | 265 |
| Ancho thumbnails | proporcional / fijo | proporcional |

### Paso 4: Procesar
1. Crear subcarpeta `thumbs/` si no existe
2. Para cada imagen:
   - Extraer número del nombre original (adaptar regex al patrón)
   - Convertir PNG → WebP (calidad confirmada)
   - Generar thumbnail (altura confirmada, ancho proporcional)
   - Guardar como `{ref}-{NNN}.webp` con padding confirmado
   - Eliminar PNG original tras conversión exitosa
3. Verificar que no quedan PNG
4. Eliminar script temporal

## Estructura resultante

```
collections/{carpeta}/
├── {ref}-001.webp
├── {ref}-002.webp
└── thumbs/
    ├── {ref}-001.webp
    ├── {ref}-002.webp
```

## Script de referencia

El agente debe generar un script PHP dinámico usando los datos recopilados.
Estructura mínima:

```php
<?php
// Estos valores se obtienen del usuario en cada ejecución
$ref        = 'CRO-REF';            // preguntado al usuario
$collection = 'carpeta-coleccion';   // detectada o preguntada
$maxHeight  = 265;                   // preguntado o default
$quality    = 85;                    // preguntado o default
$padding    = 3;                     // preguntado o default

$base   = __DIR__ . '/collections/' . $collection;
$thumbs = $base . '/thumbs';
if (!is_dir($thumbs)) mkdir($thumbs, 0755, true);

$files = glob($base . '/*.png'); // adaptar extensión
sort($files);

foreach ($files as $path) {
    $name = basename($path);
    // Adaptar regex al patrón de nombre original
    preg_match('/PATTERN(\d+)\.\w+/', $name, $m);
    if (!isset($m[1])) continue;

    $num  = (int) $m[1];
    $file = $ref . '-' . str_pad($num, $padding, '0', STR_PAD_LEFT);

    $src = imagecreatefrompng($path);
    if (!$src) continue;
    imagepalettetotruecolor($src);
    imagewebp($src, $base . '/' . $file . '.webp', $quality);

    $w  = imagesx($src);
    $h  = imagesy($src);
    $tw = (int) round($w * ($maxHeight / $h));

    $thumb = imagecreatetruecolor($tw, $maxHeight);
    imagesavealpha($thumb, true);
    $tr = imagecolorallocatealpha($thumb, 0, 0, 0, 127);
    imagefill($thumb, 0, 0, $tr);
    imagecopyresampled($thumb, $src, 0, 0, 0, 0, $tw, $maxHeight, $w, $h);
    imagewebp($thumb, $thumbs . '/' . $file . '.webp', $quality);

    imagedestroy($src);
    imagedestroy($thumb);
    unlink($path);
}
echo "COMPLETADO";
```

## Notas

- Adaptar la regex según el patrón de nombre de los PNG originales
- Si las imágenes son JPG, usar `imagecreatefromjpeg()` en lugar de `imagecreatefrompng()`
- Eliminar siempre el script temporal al finalizar
- Ofrecer hacer commit y push al finalizar
