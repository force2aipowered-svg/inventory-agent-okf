Bundle: JUEGO DE MESA

Descripción general:
Catálogo para juegos de mesa, cajas, componentes y accesorios relacionados.

Campos y reglas (instrucciones):
- id: identificador único del registro. Obligatorio.
- nombre: título del juego (ej. "Catan"). Recomendado y altamente recomendable al añadir.
- jugadores_min: número mínimo de jugadores estimado. Recomendado si es detectable.
- jugadores_max: número máximo de jugadores estimado.
- duracion_minutos: duración aproximada en minutos. Opcional.
- componentes: lista de componentes detectables o reportados (ej. "tablero", "cartas", "fichas"). Recomendado.
- editorial: editorial o fabricante, si se detecta. Opcional.
- condicion: "nuevo", "usado", "incompleto", "defectuoso". Recomendado.
- fotos: lista de URLs de imágenes asociadas. Al menos 1 foto obligatoria al añadir.
- notas: texto libre para observaciones.
- atributos_libres: para metadatos adicionales.

Reglas de ingestión desde foto (añadir):
- Priorizar fotos de la caja y de los componentes sueltos para identificar el juego.
- Si no se puede determinar el nombre, crear registro con estado "pendiente-de-identificacion" y permitir búsqueda por similitud de imagen o revisión humana.

Observaciones:
- Registrar si faltan componentes importantes y marcar el registro como "incompleto" cuando aplique.
