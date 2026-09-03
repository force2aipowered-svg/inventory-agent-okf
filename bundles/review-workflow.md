Flujo de revisión humana (INSTRUCCIONES)

1) Señalamiento de registros
- Situaciones que disparan revisión humana:
  - registros con estado 'pendiente-de-revision' o 'pendiente-de-identificacion'
  - baja confianza del clasificador automático
  - campos obligatorios faltantes
  - conflicto en detección de atributos críticos (p. ej. condición 'defectuoso' detectado por IA)

2) Cola de revisores
- Mantener una cola priorizada por antigüedad y criticidad (registros con incompletitud crítica primero).
- Cada item en la cola debe presentar:
  - fotos (todas las disponibles)
  - metadatos extraídos automáticamente (OCR, etiquetas detectadas)
  - campos faltantes sugeridos
  - botón/acción para: 'Completar metadatos', 'Confirmar identidad del objeto', 'Marcar como inapropiado', 'Asignar a otro revisor'

3) Acciones del revisor
- Completar los campos faltantes y marcar la fuente como 'revision_humana'.
- Cambiar estado a 'activo' o 'incompleto' según corresponda.
- Añadir notas obligatorias cuando se realicen cambios críticos.

4) Escalado
- Si el revisor no puede identificar el objeto, escalar a un equipo especializado o marcar para subida de más fotos / interacción con el usuario.

5) Historial y trazabilidad
- Registrar quién revisó, qué cambios realizó y por qué.
- Vincular la acción de revisión a la auditoría general.
