# Arquitectura propuesta con SQL Server y Power BI

## Objetivo

Simular un entorno real de inteligencia de negocios sin modificar los archivos oficiales. La arquitectura separa fuente, procesamiento, almacenamiento, consumo y gobierno para que cada resultado pueda rastrearse hasta un archivo crudo.

```text
data.gouv.fr / CSV oficiales
             |
             v
data/raw (solo lectura, Git LFS, SHA-256)
             |
             v
Python + Jupyter (perfilamiento, ETL, pruebas y bitácora)
             |
             +--------------------> data/processed (CSV/Parquet regenerable)
             |
             v
SQL Server Developer
  raw_control -> stg_vacunacion -> dw_vacunacion -> mart_cobertura
             |
             +--------------------> consultas de control y vistas SQL
             |
             v
Power BI Desktop <---- GeoJSON de 103 departamentos
             |
             +----> tablero, seis vistas, tres KPI y PDF
             |
             v
Informe, prueba de usabilidad, video y defensa

Git + Git LFS + GitHub versionan datos crudos, código y documentación.
```

## Herramientas y función

| Capa | Herramienta | Uso concreto | Evidencia |
|---|---|---|---|
| Fuente | data.gouv.fr | Origen oficial, licencia y enlaces | ficha de datos y README |
| Versiones | Git + Git LFS + GitHub | historial del proyecto y CSV grandes | commits, etiquetas y repositorio |
| Desarrollo | Visual Studio Code | editar Python, SQL y Markdown | archivos fuente |
| Análisis | Python 3 + pandas + Jupyter | perfilamiento, ETL, estadística y pruebas | notebooks y scripts ejecutables |
| Conexión | `pyodbc` + ODBC Driver for SQL Server | carga controlada desde Python | script y registro de carga |
| Base | SQL Server Developer | entorno local completo para aprendizaje | base y scripts DDL/DML |
| Administración | SQL Server Management Studio | ejecutar, revisar y respaldar | capturas y consultas de validación |
| BI | Power BI Desktop | modelo semántico, DAX, mapa, filtros y tablero | PBIX y PDF |
| Geoespacial | QGIS | inspeccionar CRS, geometría y uniones | proyecto QGZ o capturas de control |
| Documentación | Markdown + PDF | trazabilidad, informe y anexos | README, documentos y PDF final |

Se recomienda **SQL Server Developer** para el entorno local porque permite practicar características del motor sin usarlo en producción. SQL Server Express sería más limitado. La publicación del tablero en Power BI Service será opcional y dependerá de la cuenta/licencia disponible; el PBIX y el PDF son entregables locales suficientes para conservar la evidencia.

## Organización lógica de SQL Server

Una sola base llamada `BI_Vacunacion_Francia` con esquemas que expresan el avance del dato:

| Esquema | Contenido | Regla |
|---|---|---|
| `ctl` | archivos, fecha de carga, hash, filas esperadas/recibidas, estado y errores | una fila de control por archivo y ejecución |
| `stg` | copia tipada de las columnas necesarias de los CSV | se recarga de forma repetible; sin métricas inventadas |
| `dw` | calendario, territorio, edad, sexo, vacuna, población y observaciones de vacunación | llaves y relaciones validadas |
| `mart` | vistas o tablas agregadas mensuales para el tablero | solo reglas documentadas y reproducibles |

Los nombres definitivos de las tablas se fijarán después del perfilamiento. No se crearán tablas innecesarias solo para aparentar complejidad.

## Flujo de carga mensual simulado

Aunque la fuente descargada es un corte histórico cerrado, el proyecto simulará el procedimiento empresarial de una carga mensual:

1. Registrar nombre, URL, fecha, tamaño y SHA-256 del archivo recibido.
2. Evitar cargar dos veces el mismo archivo mediante el hash y una clave de lote.
3. Validar separador, codificación, encabezado, tipos, rango de fechas y cantidad de columnas.
4. Cargar primero en `stg` con un identificador de lote.
5. Rechazar o aislar filas que incumplan una regla explícita; nunca eliminarlas en silencio.
6. Actualizar estructuras analíticas por clave natural y fecha.
7. Comparar filas, sumas y cobertura antes y después.
8. Refrescar el modelo de Power BI y registrar el resultado.

No se afirmará que existen nuevas publicaciones mensuales después de julio de 2023. La simulación dividirá el histórico por mes para demostrar incrementalidad sin fabricar observaciones.

## Seguridad y privacidad

- Los datos son agregados y anónimos; no incluyen identificadores individuales.
- La base se ejecutará localmente con una cuenta de mínimo privilegio para el ETL.
- Contraseñas y cadenas de conexión irán en variables de entorno, nunca en Git.
- `data/raw` será de solo lectura dentro del proceso.
- Los respaldos `.bak` no se publicarán automáticamente.
- La publicación incluirá atribución, licencia y límites de interpretación.

## Recuperación y reproducibilidad

La base no será el único artefacto. Todo objeto deberá poder reconstruirse con scripts en `sql/`, la configuración documentada y los notebooks/scripts de `python/`. Los productos regenerables se guardarán en `data/processed`, pero los archivos grandes de salida no se duplicarán en Git si pueden reconstruirse.

