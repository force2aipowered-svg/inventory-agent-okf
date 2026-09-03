Especificación de la carga cuando se envía una foto al agente (INSTRUCCIONES — no es un esquema en JSON):

1) Campos esperados en la carga de una foto
- action: acción solicitada. Valores permitidos: "añadir", "revisar", "eliminar", "modificar".
- photo_url o photo_base64: referencia a la foto (URL pública) o foto codificada en base64. Debe incluirse una de las dos.
- object_type: opcional. Si el cliente lo conoce puede enviarlo; si no, el receptor debe clasificar el tipo automáticamente.
- object_id: requerido cuando la acción es "revisar", "eliminar" o "modificar" (identificador del objeto existente).
- metadata: objeto libre con atributos proporcionados por el cliente (por ejemplo: talla, color, nota, componentes). Cada bundle define sus campos esperados.
- user_id: identificador del remitente.
- timestamp: hora del envío (si no viene, el receptor debe asignarla).
- source_device_id: opcional, identificación del dispositivo origen.

2) Reglas generales de validación
- Siempre validar la presencia de "action" y de una imagen (photo_url o photo_base64).
- Si action es "añadir" y falta información crítica según el catálogo, se permite crear el registro incompleto y marcarlo como "pendiente de revisión".
- Para acciones que requieren object_id, devolver error si no es proporcionado o no existe.

3) Clasificación de tipo de objeto
- Paso inicial: si object_type no fue enviado, clasificar la foto en tipos conocidos (por ahora: "Ropa", "Juego de Mesa", o "otro").
- El receptor debe soportar un resultado "otro" para elementos no contemplados por los bundles existentes.

4) Metadatos y extensibilidad
- metadata puede contener campos arbitrarios. Los bundles especifican campos obligatorios y recomendados para cada tipo.
- El sistema debe aceptar atributos adicionales y almacenarlos en un campo genérico (atributos_libres) si no están en el schema del bundle.

5) Seguridad y permisos (instrucciones)
- Las acciones "eliminar" y "modificar" deben verificarse contra permisos del user_id o roles relacionados.
- Registrar auditoría: quién solicitó la acción, cuándo y cuál fue el resultado.

6) Respuestas esperadas (instrucciones para implementadores)
- Responder con un objeto que indique estado (ok/error), action procesada, object_type detectado, object_id (si corresponde) y mensajes de validación.
- En caso de crear un registro incompleto, incluir una lista de campos faltantes y un estado "pendiente-de-revisión".
