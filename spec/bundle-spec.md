Instrucciones para definir un bundle OKF (plantilla de descriptor — en lenguaje natural):

Cada bundle representa un catálogo de un tipo de objeto y debe contener los siguientes elementos y metadatos:

1) descriptor (descriptor.md)
- Nombre del bundle.
- Versión semántica del bundle.
- Maintainer (organización o persona responsable).
- Archivo de esquema (nombre y breve descripción).
- Archivo(s) de registros (ubicación o formato esperado: JSONL, BD, etc.).
- Licencia y contacto.

2) schema (schema.md)
- Lista de campos con:
  - Nombre del campo.
  - Tipo de dato esperado (string, entero, fecha, lista, objeto).
  - Obligatorio / Recomendado / Opcional.
  - Descripción y ejemplos de valores (en texto, sin bloques de código).
- Reglas de validación adicionales (por ejemplo, foto requerida mínimo 1, talla no vacía para ropa).

3) data/
- Ubicación prevista para los registros del bundle.
- Recomendación: usar un archivo por registro (JSONL) o una base de datos; documentar el formato y el identificador único (id).

4) media/
- Convenciones para almacenar referencias a imágenes (URLs absolutas preferidas). No almacenar binarios dentro del bundle.

5) versionado
- Cada cambio en schema debe incrementar la versión del bundle y documentarse en el descriptor.

6) ejemplo operativo (instrucciones)
- Cómo crear un nuevo registro: campos mínimos, proceso de validación, estado inicial.
- Cómo marcar registros "pendientes de revisión" y el flujo para completarlos.

Nota: en este repositorio los esquemas se expresan en lenguaje natural (README/MD). Los equipos de desarrollo pueden transformar estas instrucciones a JSON Schema u otro formato técnico según convenga.
