Flujo de procesamiento (instrucciones) — paso a paso

1) Recepción
- El sistema recibe un payload que incluye la foto y la acción (añadir/revisar/eliminar/modificar).
- Validar estructura mínima (acción + foto).

2) Clasificación de tipo
- Si el payload no incluye object_type, ejecutar clasificación automática para asignar el bundle objetivo (ropa / juego-de-mesa / otro).

3) Enrutamiento por acción
- Añadir:
  - Generar id único para el nuevo registro.
  - Extraer atributos posibles de la imagen (color, texto con OCR, componentes, etc.).
  - Solicitar o marcar campos faltantes; si la información mínima no está completa, crear registro con estado "pendiente-de-revisión".
  - Almacenar referencia a la(s) foto(s) en el campo correspondiente.
  - Responder con object_id y estado.
- Revisar:
  - Recuperar metadatos por object_id o por búsqueda por imagen cuando no haya id.
  - Devolver ficha con historial y fotos.
- Eliminar:
  - Verificar permisos y proceder a marcar como eliminado o borrar físicamente según política.
- Modificar:
  - Validar que object_id existe y que el user_id tiene permiso, aplicar cambios y actualizar fecha_actualizacion.

4) Post-procesos
- Auditoría: registrar la operación con user_id, timestamp y resultado.
- Notificaciones: cuando un registro queda "pendiente-de-revisión", notificar a revisores humanos.
- Versionado de registros: mantener historial de cambios cuando se modifique información crítica.

Notas operativas:
- Preferir la marca "soft delete" (marcar eliminado) salvo orden explícita de borrar físicamente.
- Mantener trazabilidad de la fuente de cada campo (automatico vs humano).
