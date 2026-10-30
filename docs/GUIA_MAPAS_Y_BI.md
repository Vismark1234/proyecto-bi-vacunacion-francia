# Guía de mapas y dashboard BI

## Mapa obligatorio recomendado

```text
Brecha de cobertura de esquema completo por departamento — junio de 2023
```

Archivos:

- Hecho: `vacsi-dep-2023-07-13-15h50.csv`.
- Dimensión: `data/reference/dim_departamento.csv`.
- Geometría: `spatial/departamentos_vacsi_103.geojson`.

Uniones:

```text
Hecho[dep] = DimDepartamento[dep]
GeoJSON.properties.code = DimDepartamento[dep]
```

Medidas:

```text
Cobertura = couv_complet
Brecha = 100 - couv_complet
Variación mensual = cobertura actual - cobertura mes anterior
```

Junio de 2023 es el último mes completo; julio termina el día 10.

## Preparación mensual

```sql
WITH Cortes AS (
    SELECT
        dep,
        jour,
        EOMONTH(jour) AS periodo_mes,
        couv_complet,
        couv_dose1,
        couv_rappel,
        ROW_NUMBER() OVER (
            PARTITION BY dep, EOMONTH(jour)
            ORDER BY jour DESC
        ) AS rn
    FROM FactVacunacionGeneral
)
SELECT
    dep,
    periodo_mes,
    couv_complet,
    100.0 - couv_complet AS brecha_cobertura,
    couv_dose1,
    couv_rappel
FROM Cortes
WHERE rn = 1;
```

## Páginas del dashboard

1. Resumen ejecutivo: cobertura, brecha, variación y dosis.
2. Mapa departamental: 103 territorios.
3. Tendencia: mes, trimestre y año.
4. Edad y sexo: brechas demográficas.
5. Vacunas: fabricante, dosis y participación.
6. Profesionales y residentes: comparación con población general.
7. Calidad: datos faltantes, fecha máxima y cobertura territorial.

## Visualizaciones

- mapa coroplético;
- línea mensual;
- barras de ranking;
- matriz departamento × grupo de edad;
- barras apiladas por vacuna;
- tarjetas KPI;
- distribución de coberturas;
- segmentadores de fecha, departamento, región, edad, sexo y vacuna.

## QGIS

1. Abrir `departamentos_vacsi_103.geojson`.
2. Cargar la vista mensual desde SQL Server o CSV.
3. Unir `properties.code` con `dep`.
4. Filtrar un único periodo.
5. Simbología graduada por `brecha_cobertura`.
6. Agregar leyenda, fecha, fuente y nota metodológica.

## Power BI

1. Cargar hechos y dimensiones.
2. Crear relaciones 1:N desde dimensiones.
3. Ocultar códigos técnicos en la vista de informe.
4. Mostrar nombres de departamento y región.
5. Para Shape Map, convertir el GeoJSON a TopoJSON; para QGIS se usa directamente.
6. Configurar tooltips con departamento, región, cobertura, brecha y variación.

