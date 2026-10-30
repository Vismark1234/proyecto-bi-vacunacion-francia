# Plan de ETL, análisis y carga

## Principio de trabajo

Los CSV de `data/raw` son evidencia original y no se editan. El proceso lee esos archivos, crea resultados nuevos y registra controles antes y después. Cada ejecución debe poder repetirse desde un entorno limpio.

## Etapas

### 1. Extracción y registro

- Inventariar los siete CSV, enlace oficial, licencia, fecha de descarga, tamaño y hash.
- Leer únicamente encabezados y muestras para inferir tipos; luego perfilar el archivo completo por bloques.
- Registrar periodo, cantidad de filas, columnas y granularidad.

### 2. Perfilamiento

- Medir nulos, duplicados por clave esperada, cardinalidad y rangos.
- Revisar códigos de territorio, edad, sexo y vacuna contra los catálogos documentados.
- Verificar fechas fuera del periodo y coberturas fuera de un rango razonable.
- Separar valores desconocidos de errores; el código de vacuna `8`, por ejemplo, se conserva como no documentado si la fuente no ofrece una etiqueta.

### 3. Transformación

- Convertir `jour` a fecha y los indicadores a tipos numéricos.
- Normalizar únicamente nombres auxiliares; conservar siempre los códigos originales.
- Añadir año, mes y clave mensual en la capa procesada.
- Unir los nombres de departamento y región mediante `dep`.
- Transformar columnas de métricas a una estructura analítica cuando ayude a Power BI, sin perder el nombre de la variable original.
- Agregar a mes mediante una regla apropiada: los flujos diarios se suman; los acumulados y coberturas se toman al último día disponible del mes. Esta regla se validará por indicador.

### 4. Carga a SQL Server

- Crear tablas de control y staging.
- Cargar por bloques con `pyodbc` y transacciones.
- Validar claves, tipos y conteos antes de confirmar.
- Construir las relaciones analíticas necesarias para fecha, territorio y segmentos.
- Publicar vistas mensuales para Power BI.

### 5. Validación

- Comparar filas leídas, aceptadas, rechazadas y cargadas.
- Confirmar que el total de población o coberturas no se sume entre grupos incompatibles.
- Comprobar que cada código de mapa tenga una geometría y un nombre.
- Ejecutar pruebas automáticas y guardar una bitácora por lote.

## Indicadores propuestos

Los KPI se cerrarán después de validar denominadores y significado de cada campo:

1. Cobertura de esquema completo al último periodo disponible.
2. Brecha territorial: diferencia entre un departamento y la referencia nacional o mediana departamental.
3. Variación mensual de cobertura o avance en puntos porcentuales.

Como análisis secundarios: cobertura de refuerzo, diferencia entre grupos de edad, diferencia por sexo y comparación de profesionales/residentes. No se sumarán porcentajes ni se mezclará población general con grupos especiales sin explicar el denominador.

## Seis vistas mínimas

| Vista | Propósito | Producto |
|---|---|---|
| Perfil bruto | nulos, volumen, rango, códigos y calidad | notebook + tabla resumen |
| Comparación | comparar cobertura por edad o territorio | barras ordenadas con escala común |
| Tendencia | observar evolución mensual | línea por mes con selección de territorio |
| Distribución | reconocer dispersión y territorios atípicos | histograma o caja y bigotes |
| Obligatoria | localizar brechas territoriales | mapa coroplético departamental |
| Tablero final | decidir con contexto | tres KPI, filtros y detalles bajo demanda |

## Criterios de aceptación

- Ejecución completa sin editar manualmente un CSV.
- Conteos antes/después y reglas de exclusión visibles.
- Ningún secreto dentro del repositorio.
- Mismo resultado al repetir una carga del mismo lote.
- Mapa con 103 códigos enlazables y reporte de ausencias.
- README con instrucciones suficientes para otra persona.

