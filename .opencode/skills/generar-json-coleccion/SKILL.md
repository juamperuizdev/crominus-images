---
name: generar-json-coleccion
description: >-
  Use when the user asks to create or update a collection JSON file for CROMINUS.
  Triggered by keywords like "collection.json", "JSON de la coleccion", "genera el JSON",
  "crear coleccion", or "nueva coleccion".
  Do NOT use for modifying collection images or thumbnails.
---

# Generar JSON de Colección CROMINUS

Estructura y reglas para generar el archivo `collection.json` de una colección de cromos de CROMINUS.

## Estructura del JSON

```json
{
    "id_category": 1,
    "status": 0,
    "date_start": "",
    "date_end": "",
    "price": 100,
    "reference": "CRO-XXX",
    "name": "Nombre de la Colección",
    "size": "anchoxalto",
    "description": "<p>HTML description</p>",
    "rarity": {
        "cro-fwc26-00-spe-00": "special",
        "cro-fwc26-01-mex-00": "rare"
    }
}
```

## Campos

| Campo | Tipo | Obligatorio | Descripción |
|---|---|---|---|
| `id_category` | int | si | ID de categoría (ver tabla abajo) |
| `status` | int | si | 0 = draft / 1 = activa |
| `date_start` | string | si | "YYYY-MM-DD" o "" si draft |
| `date_end` | string | si | "YYYY-MM-DD" o "" si draft |
| `price` | int | si | Precio en crominus |
| `reference` | string | si | Código único en MAYÚSCULAS, guiones como separadores |
| `name` | string | si | Nombre visible de la colección |
| `size` | string | si | "anchoxalto" (ej: "660x920", "690x920") |
| `description` | string | si | HTML con la descripción |
| `rarity` | object | si | Clave = reference del cromo (nombre de archivo sin extensión), Valor = tipo de rareza |

## Categorías disponibles

| ID | Categoría   |
|----|-------------|
| 1  | General     |
| 2  | Cine        |
| 3  | Música      |
| 4  | Historia    |
| 5  | Videojuegos |
| 6  | Deportes    |

## Tipos de rareza

| Rareza | Uso |
|---|---|
| `normal` | Cromo base estándar |
| `rare` | Cromo poco común |
| `special` | Cromo especial (ilustración especial, etc.) |
| `epic` | Cromo épico o legendario |

## Reglas de naming

- `reference` debe coincidir con el prefijo de los archivos de imagen.
  - Si las imágenes son `CRO-FWC26-001.webp`, la reference es `CRO-FWC26`.
  - Siempre en MAYÚSCULAS.
  - Separador: guiones (`-`).
- Los archivos de imagen tienen formato `{reference}-{NNN}.webp` con padding de 3 dígitos.

## Tamaños de colecciones conocidas

Revisar en `README.md` la sección "Tamaño de las imágenes" para conocer el tamaño de la colección actual.

Conocidos hasta ahora:
- Estándar: 750x1050
- Pokémon: 660x920
- Panini FIFA World Cup: 690x920

## Procedimiento

1. Confirmar con el usuario el `id_category`, `price`, `name`, `reference` y `description`.
2. Confirmar las rarezas de cada cromo. Si el usuario no especifica rarezas individuales, preguntar.
3. Generar el archivo `collections/{carpeta}/collection.json`.
4. Verificar que el JSON generado coincida con el esquema.
