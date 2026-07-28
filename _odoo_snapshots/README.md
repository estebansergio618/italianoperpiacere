# Snapshots de Odoo (italianoperpiacere.com)

Copias del contenido que está **vivo en Odoo** (campo `html_content` de cada página del curso),
para poder comparar y restaurar. Cada carpeta es una foto con fecha.

## Qué hay en cada carpeta

- `uN_<pagina>_<slide_id>.html` — el HTML exacto que estaba publicado en esa página.
- `manifest.json` — por cada página: `slide_id`, `write_date`, `sha256` y tamaño.
  Sirve para detectar si algo cambió sin tener que comparar archivo por archivo.

## Cómo generar uno nuevo

```bash
cd C:/Users/esteb/ipp-audio-tools
PYTHONIOENCODING=utf-8 ODOO_KEY=<api_key> python snapshot_odoo.py 2026-08-15-antes-de-X
```

Conviene tomar uno **antes y después** de cualquier cambio en Odoo.

## Estado de referencia

- **`2026-07-28-antes-de-quitar-U5-U8/`** — foto tomada justo antes de despublicar y archivar
  las unidades 5 a 8. Contiene las 8 unidades, así que sirve tanto para restaurar U1-U4
  como para recuperar el contenido de U5-U8 si alguna vez se retoma esa etapa.

El contenido de **U1-U4** de este snapshot es idéntico a los archivos de `CURSO 1/` del repo
(verificado con diff completo: 0 bloques distintos). Ese es el estado publicado y de referencia:
tag `curso1-4-unidades`.

## Notas

- Odoo **no guarda historial** del `html_content` de los slides: si se sobreescribe una página,
  la versión anterior solo existe en estos snapshots o en el repo. Por eso importan.
- Las páginas del curso vienen envueltas en el snippet `s_embed_code` de Odoo, que **duplica**
  el contenido (`<template class="s_embed_code_saved">` + `<div class="s_embed_code_embedded">`).
  Por eso el HTML de Odoo pesa ~2x el archivo local: no es una diferencia real.
- Unidades **1 a 4 congeladas**: no modificar. El generador (`gen_unit.py`) aborta si se le pide
  tocar esos slides.
