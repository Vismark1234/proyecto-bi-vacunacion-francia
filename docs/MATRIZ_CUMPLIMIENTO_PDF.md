# Matriz de cumplimiento del PDF

Esta matriz convierte la guía entregada en trabajo verificable. El estado inicial indica qué ya existe y qué debe producirse durante el proyecto.

| Requisito de la guía | Evidencia planificada | Ubicación | Estado al iniciar |
|---|---|---|---|
| Ruta 05 y decisión concreta | acta de alcance aprobada | `docs/ACTA_ALCANCE.md` | borrador listo |
| Fuente, licencia y periodo | documentación y enlaces oficiales | `README.md`, `LICENSE-DATA.md` | listo |
| Mínimo 500 registros y 8 variables | 4.576.292 filas; hasta 57 columnas | `README.md` | superado |
| Datos brutos sin modificar | siete CSV con SHA-256 | `data/raw`, `docs/CHECKSUMS_SHA256.txt` | listo |
| Bruto y procesado separados | carpetas independientes | `data/raw`, `data/processed` | estructura lista |
| ETL ejecutable y trazable | notebooks, scripts, SQL y bitácora | `python`, `sql`, `docs/PLAN_ETL_SQL_SERVER.md` | pendiente de desarrollar |
| Perfilamiento de datos | faltantes, tipos, distribución, sesgos y granularidad | `python/notebooks` e informe | pendiente |
| Matriz tarea–dato–visualización | justificación y riesgo de cada vista | `03_visualizaciones` o informe | pendiente |
| Seis vistas mínimas | perfil, comparación, tendencia, distribución, mapa y tablero | Power BI/PDF/PNG | pendiente |
| Mapa coroplético | cobertura/brecha por departamento | Power BI con GeoJSON | geometría disponible; visual pendiente |
| Tendencias mensuales | evolución por periodo y filtros | Power BI | pendiente |
| Tres KPI | cobertura, brecha y variación | Power BI + definición | propuestos; validar |
| Versión inicial y mejorada | capturas y registro de cambios | `03_visualizaciones` | pendiente |
| Prueba con dos personas | tareas, resultados, problemas y cambios | `06_evidencias` | pendiente |
| Accesibilidad | contraste, alternativa al color, etiquetas y texto alternativo | tablero e informe | pendiente |
| Cinco autores mínimos | Munzner, Cleveland y McGill, Few, Tufte y otro | informe con APA 7 | pendiente |
| Once fichas obligatorias | principio, decisión, evidencia y verificación | anexos del informe | pendiente |
| Normas geoespaciales | ISO 19111, 19115-1 y 19157-1 | metadatos e informe | pendiente |
| CRISP-DM, Munzner y PDCA | estructura del proceso y revisiones | informe y bitácora | planificado |
| Privacidad y ética | minimización, sesgos y límites | informe y README | base documentada; ampliar |
| Informe técnico | opción más exigente: 30 o más páginas | `05_informe` | pendiente |
| Video y defensa | video de 5–7 min + defensa/demo de 15 min | `06_evidencias` | pendiente |
| Declaración de IA | herramienta, propósito, indicación, uso y verificación | anexo | pendiente |
| Repositorio reproducible | README, estructura, versiones y enlaces | GitHub | en preparación |

## Contradicciones detectadas en la guía

La página 2 pide un informe de 30 o más páginas, mientras la página 7 indica 12–15 páginas. Se adopta el mínimo más estricto: **30 páginas sin contar anexos**, salvo instrucción escrita del docente.

La página 2 menciona video de 15 minutos y la página 7/8 pide video de 5–7 minutos. Se planifican dos evidencias: **video editado de 5–7 minutos** y **guion/demo para una defensa de hasta 15 minutos**.

La página 6 enumera IEEE 7000 y 7003 en la tabla, pero el texto añade IEEE 7001 dentro de las once fichas. Para evitar una omisión, se incluirán las once fichas citadas por el texto y se aclarará la edición consultada.

