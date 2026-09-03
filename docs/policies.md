Políticas de permisos, auditoría y retención (INSTRUCCIONES)

1) Permisos y roles
- Roles sugeridos:
  - administrador: puede añadir, revisar, modificar y eliminar cualquier registro.
  - revisor: puede marcar y completar registros "pendientes" y modificar metadatos no sensibles.
  - usuario: puede añadir registros y solicitar modificaciones sobre los propios registros; puede solicitar eliminación.
  - auditor: acceso de solo lectura a auditoría y cambios.
- Regla de autorización:
  - Para modificar o eliminar: verificar que user_id sea propietario del registro o que el actor tenga rol administrador.
  - Guardar un log de autorización que registre el role, user_id, y la decisión de permitir/denegar.

2) Auditoría (registro de eventos)
- Cada acción debe emitirse como un evento de auditoría con al menos los siguientes campos:
  - event_id (UUID)
  - timestamp
  - actor_user_id
  - actor_role
  - action (añadir/revisar/modificar/eliminar)
  - target_object_id (si aplica)
  - input_summary (campos clave del payload, sin incluir la imagen completa en base64)
  - result_status (ok/error)
  - validation_messages (lista de mensajes sobre campos faltantes o errores)
- Los logs de auditoría deben ser inmutables (append-only) y exportables por periodos.

3) Retención y privacidad
- Definir periodo de retención para imágenes y metadatos sensibles conforme a la jurisdicción aplicable.
- Para datos personales (p.ej. información de usuarios), habilitar mecanismos de eliminación o anonimización bajo solicitud.
- Mantener backups cifrados y controlar accesos al almacenamiento de objetos.

4) Operaciones de eliminación
- Soft-delete por defecto (campo estado = 'eliminado' y conservar registro para auditoría).
- Borrado físico solo mediante procesos administrativos y con registro en auditoría.

5) Acceso a imágenes
- URLs de imágenes deben ser firmadas (presigned) para accesos temporales cuando sea necesario.
- Registrar en auditoría quién solicitó acceder la imagen completa (si aplica).
