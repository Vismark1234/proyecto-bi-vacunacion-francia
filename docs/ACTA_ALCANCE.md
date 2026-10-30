# Acta de alcance individual

## Identificación

- Ruta: 05 — Cobertura de vacunación.
- Fecha de inicio: 30 de octubre de 2026.
- Duración planificada: cuatro semanas, hasta el 26 de noviembre de 2026.
- Estudiante: pendiente de completar.
- Docente y gestión: pendientes de completar.

## Decisión que apoyará el proyecto

Priorizar territorios y grupos de edad de Francia que presentan las mayores brechas de cobertura de vacunación contra la COVID-19, considerando la evolución mensual, para orientar una intervención territorial simulada.

## Pregunta principal

¿En qué departamentos y grupos de edad se observan las coberturas más bajas o estancadas, cómo cambian por mes y cuáles deberían revisarse primero?

## Audiencia

Responsable simulado de planificación sanitaria territorial que necesita comparar departamentos, edades, sexo y evolución temporal sin acceder a datos personales.

## Fuente, licencia y periodo

- Productor: Santé publique France.
- Sistema de origen: VAC-SI.
- Portal: data.gouv.fr.
- Licencia: Licence Ouverte / Open Licence 2.0.
- Periodo disponible en los archivos: 27 de diciembre de 2020 a 10 de julio de 2023.
- Granularidad principal: día, departamento y, según el archivo, edad, sexo, vacuna o tipo de población.
- Volumen: 4.576.292 filas crudas en siete CSV.

## Herramientas y evidencias

- Python y Jupyter para perfilamiento, transformación, validación y análisis reproducible.
- SQL Server Developer para staging, almacenamiento analítico, controles y consultas.
- SQL Server Management Studio para administrar y demostrar la base.
- Power BI Desktop como herramienta principal del tablero y de los KPI.
- QGIS para comprobar la geometría y calidad espacial cuando sea necesario.
- Git, Git LFS y GitHub para versiones, documentación y publicación.

## Visual obligatorio y norma focal

- Visual obligatorio: mapa coroplético y tendencias mensuales.
- Norma focal: ISO 19115-1; también se documentarán ISO 19111 e ISO 19157-1 por tratarse de una ruta geoespacial.

## Alcance incluido

- Conservación de los datos crudos sin modificación.
- ETL repetible desde CSV a SQL Server y a archivos procesados.
- Análisis por tiempo, territorio, edad, sexo, vacuna y población profesional/residente donde la fuente lo permita.
- Seis vistas mínimas, tres KPI, tablero interactivo, informe, prueba de usabilidad y evidencias.
- Recomendación limitada por los datos disponibles.

## Fuera de alcance

- Identificar pacientes, vacunadores o establecimientos.
- Inferir causalidad o efectividad clínica.
- Afirmar que el departamento de residencia es el lugar de aplicación.
- Usar estos datos históricos como descripción de la situación actual de 2026.

## Riesgo principal

Interpretar una cobertura agregada como desempeño de un centro de vacunación. La mitigación será mostrar de forma visible que el territorio corresponde a residencia, declarar el periodo histórico y documentar denominadores, faltantes y reglas de agregación.

## Diferenciación a validar con el docente

La combinación propuesta es: priorización por brecha territorial y edad, fuente VAC-SI histórica, comparación mensual por departamento, mapa coroplético departamental y arquitectura Python–SQL Server–Power BI. Debe ser aprobada por el docente antes de cerrar el ETL.

