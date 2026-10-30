# Planificación diaria del proyecto

## Resumen

- Inicio: viernes 30 de octubre de 2026.
- Fin: jueves 26 de noviembre de 2026.
- Duración: 28 días consecutivos.
- Lunes a viernes: máximo 2 horas por día.
- Sábados y domingos: máximo 5 horas por día.
- Carga total: 80 horas.
- Método: CRISP-DM para datos, modelo anidado de Munzner para visualización y PDCA para revisión.

Cada jornada termina con un archivo, una validación o una decisión registrada. Las horas incluyen documentación, no solo construcción técnica.

## Semana 1 — Comprensión, gobierno y perfilamiento (19 horas)

| Fecha | Horas | Trabajo | Resultado verificable |
|---|---:|---|---|
| Vie. 30/10 | 2 | Revisar toda la guía, cerrar pregunta, audiencia, alcance y riesgos | acta de alcance y matriz de requisitos |
| Sáb. 31/10 | 5 | Verificar fuentes, licencia, archivos, hashes, granularidad, diccionario y límites | ficha de datos y documentación revisada |
| Dom. 01/11 | 5 | Preparar entorno Python/Jupyter y notebook de perfilamiento; leer los siete CSV por bloques | entorno reproducible y carga inicial |
| Lun. 02/11 | 2 | Medir filas, tipos, nulos, cardinalidad, fechas y duplicados | tabla de calidad inicial |
| Mar. 03/11 | 2 | Perfilar territorio, edad, sexo, vacuna y poblaciones especiales | catálogos y anomalías documentadas |
| Mié. 04/11 | 2 | Analizar sesgos, privacidad, actualidad y riesgos de interpretación | sección de límites y matriz de riesgos |
| Jue. 05/11 | 1 | Revisar con PDCA lo producido y corregir trazabilidad | control de semana 1 |

Hito: fuente y licencia verificadas, pregunta diferenciada, calidad inicial y perfil bruto reproducible.

## Semana 2 — ETL y SQL Server (21 horas)

| Fecha | Horas | Trabajo | Resultado verificable |
|---|---:|---|---|
| Jue. 05/11 | 1 | Completar diseño del flujo, reglas mensuales y controles antes/después | especificación ETL |
| Vie. 06/11 | 2 | Instalar/configurar SQL Server Developer, SSMS, ODBC y base local | conexión probada y versiones registradas |
| Sáb. 07/11 | 5 | Crear scripts de base, esquemas de control/staging y tablas tipadas | DDL ejecutable desde cero |
| Dom. 08/11 | 5 | Programar carga Python por lotes, hash, auditoría e idempotencia | primer archivo cargado y reejecución segura |
| Lun. 09/11 | 2 | Incorporar limpieza, tipos, códigos y filas rechazadas con causa | transformación trazable |
| Mar. 10/11 | 2 | Implementar carga del resto de archivos y controles de conteo | siete fuentes en staging |
| Mié. 11/11 | 2 | Crear estructuras analíticas de fecha, territorio y segmentos | relaciones y claves validadas |
| Jue. 12/11 | 2 | Crear agregaciones mensuales y vistas para consumo | mart mensual consultable |

Hito: ETL ejecutable, bruto intacto, SQL Server reconstruible y validaciones de carga visibles.

## Semana 3 — Análisis, diseño y tablero (20 horas)

| Fecha | Horas | Trabajo | Resultado verificable |
|---|---:|---|---|
| Vie. 13/11 | 2 | Analizar distribuciones, faltantes, relaciones y brechas con Python | notebook analítico y hallazgos cautelosos |
| Sáb. 14/11 | 5 | Definir KPI, denominadores, medidas DAX y matriz tarea–dato–visual | especificación del tablero |
| Dom. 15/11 | 5 | Conectar Power BI a SQL Server; construir modelo, calendario, medidas y filtros | modelo Power BI funcional |
| Lun. 16/11 | 2 | Crear comparación territorial/edad y vista de distribución | dos vistas con títulos y unidades |
| Mar. 17/11 | 2 | Crear tendencias mensuales y anotaciones de periodo | serie temporal validada |
| Mié. 18/11 | 2 | Integrar GeoJSON, comprobar códigos y crear mapa coroplético | mapa con 103 territorios controlados |
| Jue. 19/11 | 2 | Montar tablero con tres KPI, filtros, reinicio y detalles | prototipo completo v1 |

Hito: seis vistas disponibles, visual obligatorio, tres KPI y primer tablero navegable.

## Semana 4 — Evaluación, informe y entrega (20 horas)

| Fecha | Horas | Trabajo | Resultado verificable |
|---|---:|---|---|
| Vie. 20/11 | 2 | Autoevaluar integridad, color, contraste, texto alternativo y escalas | lista de accesibilidad y correcciones |
| Sáb. 21/11 | 5 | Realizar prueba con dos personas, registrar tareas, tiempos, errores y comentarios | protocolo, resultados y consentimiento básico |
| Dom. 22/11 | 5 | Aplicar mejoras; documentar versión inicial/final y completar fichas normativas | tablero v2 y anexos normativos |
| Lun. 23/11 | 2 | Redactar método, fuente, ETL, análisis, autores y normas con APA 7 | borrador del informe completo |
| Mar. 24/11 | 2 | Redactar resultados, recomendación, límites y bitácora de IA | informe de 30+ páginas revisado |
| Mié. 25/11 | 2 | Exportar PBIX/PDF/capturas; grabar video de 5–7 min y ensayar defensa de 15 min | paquete de evidencias |
| Jue. 26/11 | 2 | Ejecutar reproducción final, verificar enlaces/archivos, etiquetar `v1.0.0` y entregar | checklist firmado y versión final |

Hito: solución reproducible, probada, documentada y lista para defensa.

## Distribución de las 80 horas

| Área | Horas aproximadas |
|---|---:|
| Alcance, fuente, calidad, ética y planificación | 14 |
| Python, perfilamiento y análisis | 12 |
| ETL y SQL Server | 18 |
| Modelo, DAX, visuales y tablero | 17 |
| Usabilidad, accesibilidad y mejora | 7 |
| Informe, normas, video, defensa y entrega | 12 |
| **Total** | **80** |

## Regla de seguimiento diario

Al finalizar cada día se registrará: tiempo real, archivo modificado, prueba realizada, resultado, problema encontrado y siguiente acción. Si una tarea tarda más, se mueve trabajo no crítico al backlog; nunca se excede el máximo diario definido.
