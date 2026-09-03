Recomendaciones de almacenamiento (INSTRUCCIONES)

Opciones de almacenamiento para fotos y metadatos:

1) Fotos (media)
- Preferible: almacenamiento de objetos (S3, MinIO o equivalente). Guardar sólo URLs públicas o firmadas en los registros del bundle.
- Alternativa para demos: almacenamiento de archivos en un servidor y servir por URL. No almacenar binarios dentro del repositorio del bundle.
- Convenciones: incorporar metadatos de la imagen (resolución, tamaño, hash) junto con la URL para permitir verificación e integridad.

2) Metadatos (registros)
- Para producción: usar una base de datos (SQL/NoSQL) con índices por id, tipo, fecha y estado.
- Para demostraciones o intercambio OKF: usar archivos JSONL en la carpeta data/ del bundle y documentar el formato en el descriptor.

3) Backups y retención
- Mantener políticas de retención de imágenes y datos personales (GDPR u otras regulaciones aplicables).
- Realizar backups periódicos de los datasets y del almacenamiento de objetos.
