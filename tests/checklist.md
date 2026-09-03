Checklist de pruebas de aceptación (INSTRUCCIONES)

1) Validación básica
- [ ] Enviar payload con action='añadir' y photo_url válido -> recibir status ok y object_id.
- [ ] Enviar payload sin image -> recibir 400.
- [ ] Enviar action que necesita object_id sin object_id -> recibir 400.

2) Clasificación
- [ ] Enviar fotos representativas de ropa -> sistema clasifica 'ropa' o devuelve 'otro' si incierto.
- [ ] Enviar fotos de juegos de mesa -> clasifica 'juego-de-mesa' o 'otro'.

3) Reglas de ingestión
- [ ] Añadir prenda con metadata completa -> estado 'activo'.
- [ ] Añadir prenda con metadata mínima -> crear y marcar 'pendiente-de-revision'.
- [ ] Añadir juego sin nombre -> crear y marcar 'pendiente-de-identificacion'.

4) Permisos y auditoría
- [ ] Intentar modificar/eliminar sin permisos -> recibir 403 y log de auditoría con denegación.
- [ ] Modificar con permisos -> registro actualizado y evento de auditoría creado.

5) Revisión humana
- [ ] Poner registro en cola de revisión y completarlo -> estado cambia a 'activo' y se registra quien lo aprobó.

6) Retención y eliminación
- [ ] Verificar soft-delete: el registro ya no aparece en búsquedas normales pero existe en auditores.
- [ ] Solicitar borrado físico según política y confirmar registro de auditoría.

Notas:
- Cada ítem debe documentarse con pasos exactos de prueba y datos de ejemplo (usar los records.jsonl añadidos en los bundles como base).
