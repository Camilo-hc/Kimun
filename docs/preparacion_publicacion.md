# Preparación de la publicación de Kimün

Estado: **APTO PARA PUBLICAR como prototipo de portafolio**. Los permisos de los
materiales entregados se consideran aclarados por la confirmación del responsable
del repositorio. La verificación local descrita abajo terminó correctamente.
Esta verificación precede a la publicación del proyecto con un historial Git nuevo.

## Confirmación y decisión sobre los materiales

El responsable del repositorio confirmó que toda la información fue entregada
libremente y preparada para su uso y publicación en un repositorio. Con base en
esa confirmación, se conservan los materiales originales y sus atribuciones.
No se verificó un documento de autorización independiente. No se atribuyen
nuevos derechos de autor ni una validación institucional de la aplicación.
Los ejemplos de fuentes institucionales no se reclasifican como datos sintéticos.
Este registro no reproduce información personal ni copias de los ejemplos.

| Archivo | Función y dependencia | Procedencia y decisión |
|---|---|---|
| `contexto/ocr-presentacion.md` | Contexto del desafío; no lo lee la aplicación. Lo referencia el índice documental. | Transcripción institucional, conservada según la confirmación del responsable. |
| `contexto/faq_integra_2.md` | Documenta respuestas y decisiones de alcance; no es una entrada de ejecución. | Correspondencia institucional, conservada según la misma confirmación. |
| `datos/rubrica_integra.json` | Entrada obligatoria de `cargar_demo`; también la usan herramientas y pruebas de evaluación. | Borrador institucional conservado sin sustituir sus datos ni alterar sus dependencias. |
| `docs/marca/logo-integra.jpg` | Referencia documental de la paleta; no se sirve en la aplicación. | Marca institucional conservada con su atribución. |
| `docs/marca/logo-kimun.pdf` | Fuente de diseño; la aplicación usa variantes exportadas. | Conservado junto con sus variantes según la confirmación del responsable; no se inventa una autoría individual. |

La confirmación comprende también el boceto, los iconos, los logos exportados y
los extractos curriculares suministrados. Los avisos existentes se conservan en
[THIRD_PARTY_NOTICES.md](../THIRD_PARTY_NOTICES.md). No se implementará la alternativa
de una rúbrica sintética propuesta antes de esta aclaración.

## Correcciones realizadas

- Añadidos los avisos completos de Pico.css 2.1.1 y HTMX 2.0.11, sin cambiar las bibliotecas.
- Conservados la licencia MIT y el copyright original del proyecto, y el aviso OFL de la fuente.
- Ampliado `.gitignore` para bases SQLite, auxiliares, respaldos, secretos, logs y temporales.
- Aclarados el historial Git nuevo, los créditos colaborativos y el carácter de prototipo.
- Sustituidos una ruta personal y una contraseña fija de ejemplo en documentación.

## Verificación técnica y límites

Verificación local realizada el 26 de octubre de 2026:

- Entorno aislado `kimun/.venv`, Python 3.12.14; instalación de las versiones
  declaradas en `requirements-dev.txt` y `requirements.txt`, sin cambiarlas.
- `python -m pip check`: sin dependencias incompatibles declaradas.
- Django 5.2.18, `check`: sin problemas (0 silenciados).
- `makemigrations --check --dry-run`: sin cambios pendientes de generar.
- `migrate --noinput`: aplicado correctamente sobre una base SQLite desechable;
  `migrate --check`: sin migraciones pendientes en esa base.
- Suite completa: **1230 passed in 480.88s**. Se utilizó pytest con
  `-q -p no:cacheprovider --durations=10 --tb=short` y un directorio temporal propio.
  La carga explícita de `pytest_django.plugin` evitó cargar plugins externos.
- Un envoltorio temporal aisló variables de configuración y credenciales, desactivó
  el acceso a metadatos EC2 y bloqueó resolución DNS y conexiones de sockets antes
  de importar Django o pytest. Las pruebas utilizaron los clientes AWS simulados.
- Las comprobaciones estáticas previas encontraron 141 archivos Python y 14 JSON
  válidos, sin enlaces locales Markdown faltantes.

Se eliminaron el envoltorio, la base de validación y los temporales después de la
verificación. El entorno virtual local se conserva y está excluido por `.gitignore`.
No se ejecutaron despliegues ni llamadas reales a AWS. Esta ejecución no es un
estado de CI, una evaluación de efectividad pedagógica ni una prueba de los
servicios AWS en producción. Tampoco verifica una migración sobre bases productivas.

## Comprobación del recorrido local documentado

Se revisó el README contra el código y se comprobó el recorrido sin AWS con una
base temporal nueva y los datos ficticios incluidos. El cliente HTTP de Django
pudo iniciar sesión como educadora y directora y obtener respuestas 200 en inicio
(siguiendo su redirección normal), curso, ficha, revisión, informe familiar y panel
del jardín. Una nota de texto nueva quedó en estado pendiente y sin observaciones
generadas, como corresponde cuando los workers no se ejecutan.

No hubo intentos de conexión de red; DNS y sockets estaban bloqueados. Esta
comprobación no sustituye una revisión visual del navegador ni valida el flujo
completo de IA. El README distingue ahora la exploración local del procesamiento
con servicios AWS propios e indica que no hay una demo pública alojada actualmente.

## Pendientes antes del uso operativo con datos reales

- Evitar nombres y respuestas crudas en logs y definir acceso y retención.
- Reintentar de manera independiente los borrados fallidos de capturas y hojas;
  establecer retención de originales, texto, historial, respaldos y vocabularios.
- Alinear el límite de audio aceptado con el umbral de subida en memoria.
- Revisar el transporte HTTP al origen CloudFront, su control de acceso, los
  parámetros del entorno y las credenciales de demo en salidas de despliegue.
- Validar las reglas pedagógicas y las integraciones antes del uso operativo.

La confirmación de publicación de los materiales no resuelve esos pendientes
operativos. La publicación del prototipo y su utilización con nuevos datos
personales reales son decisiones distintas.
