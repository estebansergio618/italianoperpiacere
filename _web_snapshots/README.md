# Snapshots de las páginas del sitio (website.page / ir.ui.view)

Copias del `arch_db` de las landings, para poder comparar y restaurar.
Odoo **no guarda historial** del contenido de estas páginas.

## Restaurar una página

Escribir el contenido del `.xml` en el campo `arch_db` de esa vista:
`ir.ui.view.write([<view_id>], {'arch_db': <contenido del archivo>})`

El nombre del archivo indica la página y el id de la vista: `home__view567.xml`.

## Ojo con estas páginas

- El contenido es **HTML crudo dentro del snippet `s_embed_code`** ("Insertar código"),
  no bloques editables normales. Por eso aparece **dos veces** en el arch: una en
  `<template class="s_embed_code_saved">` y otra en `<div class="s_embed_code_embedded">`.
  Solo la segunda se ve; la primera es la que usa el editor. **Si se edita una sola,
  quedan desincronizadas.**
- Consecuencia práctica: el cliente **no puede** cambiar estos textos con el editor
  visual de Odoo (doble clic). Necesita el editor de código del snippet.
  Por eso los datos volátiles (precios, fechas) no deben vivir acá.
- Hay **dos páginas con URL `/`**: vistas 567 (la real, ~109k) y 559 (~213 chars).

## Carpetas

- `2026-07-28-antes-de-centralizar-precios/` — antes de quitar precios/fechas del home.
- `2026-07-28-despues-de-centralizar-precios/` — después.
