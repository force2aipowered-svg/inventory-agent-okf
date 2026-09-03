Bundle: ROPA

Descripción general:
Catálogo para prendas de vestir y accesorios. Este documento especifica los campos esperados, cuáles son obligatorios y recomendaciones para la ingestión a partir de fotos.

Campos y reglas (instrucciones):
- id: identificador único del registro (UUID recomendado). Obligatorio al almacenar.
- nombre: nombre amigable de la prenda (ej. "Camisa azul de manga larga"). Recomendado.
- categoria: tipo general (ej. "camisa", "pantalón", "vestido", "chaqueta"). Obligatorio o generar a partir de la clasificación de imagen.
- talla: información de talla (ej. "M", "38", "S"). Recomendado para ropa.
- color: color principal detectado o proporcionado. Recomendado.
- marca: marca o etiqueta (si se puede detectar por OCR o input). Opcional.
- material: algodón, poliéster, etc. Opcional.
- condicion: valores posibles: "nuevo", "usado", "defectuoso". Recomendado.
- fotos: lista de URLs a las imágenes asociadas. Al menos 1 foto obligatoria al añadir.
- fecha_creacion, fecha_actualizacion: marcas temporales.
- atributos_libres: objeto para metadatos adicionales (sin estructura rígida).

Reglas de ingestión desde foto (añadir):
- Se debe intentar extraer categoria, color y cualquier texto visible mediante OCR.
- Si falta talla o categoria, el sistema puede crear el registro y marcarlo como "pendiente-de-revisión".
- Almacenamiento de fotos: preferir URLs a un almacenamiento externo y guardar la referencia en el campo photos.

Observaciones:
- Mantener una sección de notas y observaciones para cada registro.
- Registrar la fuente del dato (usuario, clasificador automático, revisión humana).
