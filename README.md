# Documentación de los datos crudos de vacunación VAC-SI

## 1. ¿Qué se descargó?

Se descargaron siete archivos CSV de vacunación contra la COVID-19 publicados por **Santé publique France** en el portal oficial de datos abiertos del Gobierno francés.

Los archivos proceden del sistema **VAC-SI**, creado a partir de la información registrada durante la campaña de vacunación francesa. Los datos publicados son reales, oficiales, agregados y anónimos.

No se modificaron, resumieron ni recortaron las filas de los CSV descargados. Los archivos conservados en `data/raw` son las copias crudas obtenidas de la fuente.

## 2. Fuente oficial

### Población general

Página oficial:

<https://www.data.gouv.fr/datasets/donnees-relatives-aux-personnes-vaccinees-contre-la-covid-19-1>

Nombre de la publicación: **Données relatives aux personnes vaccinées contre la Covid-19**.

### Profesionales y residentes

Página oficial:

<https://www.data.gouv.fr/datasets/donnees-de-vaccination-relatives-aux-professionnels-et-resident-en-ehpad-et-usld>

Nombre de la publicación: **Données de vaccination relatives aux professionnels et résident en Ehpad et USLD**.

### Productor y licencia

- Productor: Santé publique France.
- Portal: data.gouv.fr.
- Licencia declarada: Licence Ouverte / Open Licence 2.0.
- Fecha de publicación de estos archivos: 13 de julio de 2023.
- Última fecha encontrada dentro de los datos: 10 de julio de 2023.

La fecha que aparece en el nombre del archivo es la fecha de publicación, no necesariamente la última fecha interna.

## 3. Ubicación de los archivos descargados

```text
data/raw/
├── poblacion_general/
│   ├── vacsi-dep-2023-07-13-15h50.csv
│   ├── vacsi-a-dep-2023-07-13-15h50.csv
│   ├── vacsi-s-dep-2023-07-13-15h51.csv
│   ├── vacsi-v-dep-2023-07-13-15h51.csv
│   └── vacsi-s-a-dep-2023-07-13-15h51.csv
└── profesionales_residentes/
    ├── vacsi-prof-dep-2023-07-13-15h51.csv
    └── vacsi-resid-dep-2023-07-13-15h51.csv
```

## 4. Resumen general verificado

| Característica | Resultado |
|---|---:|
| Archivos crudos | 7 |
| Filas totales | 4.576.292 |
| Tamaño total | 490,92 MB |
| Primera fecha | 27 de diciembre de 2020 |
| Última fecha | 10 de julio de 2023 |
| Frecuencia | Diaria |
| Territorios de población general | 103 |
| Territorios de profesionales y residentes | 102 |
| Grupos de edad | 15 |
| Categorías de sexo | 3 |
| Códigos de vacuna | 12 |
| Mayor cantidad de columnas | 57 |
| Filas con estructura incorrecta encontradas | 0 |

La población general contiene también el territorio `977`, Saint-Barthélemy. Este código no aparece en las tablas de profesionales y residentes, por lo que esas tablas tienen 102 territorios.

## 5. Inventario y enlaces directos de descarga

### 5.1 Cobertura general por departamento

Archivo: `vacsi-dep-2023-07-13-15h50.csv`

- 95.378 filas.
- 20 columnas.
- Tamaño: 7,88 MB.
- Una fila representa un departamento en una fecha.

Descarga oficial directa:

<https://static.data.gouv.fr/resources/donnees-relatives-aux-personnes-vaccinees-contre-la-covid-19-1/20230713-135040/vacsi-dep-2023-07-13-15h50.csv>

### 5.2 Vacunación por departamento y grupo de edad

Archivo: `vacsi-a-dep-2023-07-13-15h50.csv`

- 1.430.670 filas.
- 21 columnas.
- Tamaño: 108,44 MB.
- Una fila representa un departamento, un grupo de edad y una fecha.

Descarga oficial directa:

<https://static.data.gouv.fr/resources/donnees-relatives-aux-personnes-vaccinees-contre-la-covid-19-1/20230713-135109/vacsi-a-dep-2023-07-13-15h50.csv>

### 5.3 Vacunación por departamento y sexo

Archivo: `vacsi-s-dep-2023-07-13-15h51.csv`

- 286.134 filas.
- 21 columnas.
- Tamaño: 23,81 MB.
- Una fila representa un departamento, una categoría de sexo y una fecha.

Descarga oficial directa:

<https://static.data.gouv.fr/resources/donnees-relatives-aux-personnes-vaccinees-contre-la-covid-19-1/20230713-135107/vacsi-s-dep-2023-07-13-15h51.csv>

### 5.4 Vacunación por departamento y tipo de vacuna

Archivo: `vacsi-v-dep-2023-07-13-15h51.csv`

- 1.144.536 filas.
- 21 columnas.
- Tamaño: 69,06 MB.
- Una fila representa un departamento, un código de vacuna y una fecha.

Descarga oficial directa:

<https://static.data.gouv.fr/resources/donnees-relatives-aux-personnes-vaccinees-contre-la-covid-19-1/20230713-135144/vacsi-v-dep-2023-07-13-15h51.csv>

### 5.5 Vacunación por departamento, edad y sexo

Archivo: `vacsi-s-a-dep-2023-07-13-15h51.csv`

- 1.430.670 filas.
- 57 columnas.
- Tamaño: 275,14 MB.
- Una fila representa un departamento, un grupo de edad y una fecha.
- Las cantidades y coberturas de hombres, mujeres y total aparecen en grupos separados de columnas.

Descarga oficial directa:

<https://static.data.gouv.fr/resources/donnees-relatives-aux-personnes-vaccinees-contre-la-covid-19-1/20230713-135210/vacsi-s-a-dep-2023-07-13-15h51.csv>

### 5.6 Cobertura de profesionales EHPAD/USLD

Archivo: `vacsi-prof-dep-2023-07-13-15h51.csv`

- 94.452 filas.
- 8 columnas.
- Tamaño: 3,63 MB.
- Una fila representa un departamento y una fecha.
- Contiene coberturas de los profesionales identificados en establecimientos para adultos mayores dependientes y unidades de cuidado de larga duración.

Descarga oficial directa:

<https://static.data.gouv.fr/resources/donnees-de-vaccination-relatives-aux-professionnels-et-resident-en-ehpad-et-usld/20230713-135146/vacsi-prof-dep-2023-07-13-15h51.csv>

### 5.7 Cobertura de residentes EHPAD/USLD

Archivo: `vacsi-resid-dep-2023-07-13-15h51.csv`

- 94.452 filas.
- 6 columnas.
- Tamaño: 2,96 MB.
- Una fila representa un departamento y una fecha.
- Contiene coberturas de residentes identificados en establecimientos para adultos mayores dependientes y unidades de cuidado de larga duración.

Descarga oficial directa:

<https://static.data.gouv.fr/resources/donnees-de-vaccination-relatives-aux-professionnels-et-resident-en-ehpad-et-usld/20230713-135122/vacsi-resid-dep-2023-07-13-15h51.csv>

## 6. ¿Qué significa la ubicación?

La columna `dep` es el código del departamento o territorio asociado a la residencia de la persona vacunada. No representa necesariamente el lugar físico donde se aplicó la vacuna.

Ejemplos de códigos:

| Código | Territorio |
|---|---|
| `75` | Paris |
| `69` | Rhône |
| `13` | Bouches-du-Rhône |
| `971` | Guadeloupe |
| `972` | Martinique |
| `973` | Guyane |
| `974` | La Réunion |
| `976` | Mayotte |
| `977` | Saint-Barthélemy |
| `978` | Saint-Martin |

Los nombres no están escritos dentro de los CSV crudos: la fuente entrega códigos geográficos. La documentación oficial señala que estos códigos siguen la codificación geográfica francesa.

## 7. Formato de los CSV

- Codificación: UTF-8.
- Separador de columnas: punto y coma (`;`).
- Formato de fecha: `YYYY-MM-DD`.
- Separador decimal: punto (`.`).
- Las coberturas están expresadas como porcentaje entre 0 y 100.
- Los códigos deben leerse como texto para conservar valores como `01`, `04`, `2A` y `2B`.

## 8. Diccionario de campos comunes

### Campos de identificación

| Campo | Significado |
|---|---|
| `dep` | código del departamento o territorio de residencia |
| `jour` | fecha del dato o de la inyección |
| `clage_vacsi` | código del grupo de edad |
| `sexe` | código de sexo |
| `vaccin` | código del tipo de vacuna |

### Cantidades diarias

| Campo | Significado |
|---|---|
| `n_dose1` | personas que recibieron una primera dosis ese día |
| `n_dose2` | personas que recibieron una segunda dosis ese día |
| `n_dose3` | personas que recibieron una tercera dosis ese día |
| `n_dose4` | personas que recibieron una cuarta dosis ese día |
| `n_complet` | personas que completaron su esquema inicial ese día |
| `n_rappel` | personas con primer refuerzo registrado ese día |
| `n_2_rappel` | personas con segundo refuerzo registrado ese día |
| `n_3_rappel` | personas con tercer refuerzo registrado ese día |
| `n_rappel_biv` | personas con refuerzo bivalente registrado ese día |

### Cantidades acumuladas

| Campo | Significado |
|---|---|
| `n_cum_dose1` | primera dosis acumulada hasta la fecha |
| `n_cum_dose2` | segunda dosis acumulada hasta la fecha |
| `n_cum_dose3` | tercera dosis acumulada hasta la fecha |
| `n_cum_dose4` | cuarta dosis acumulada hasta la fecha |
| `n_cum_complet` | esquemas iniciales completos acumulados |
| `n_cum_rappel` | primeros refuerzos acumulados |
| `n_cum_2_rappel` | segundos refuerzos acumulados |
| `n_cum_3_rappel` | terceros refuerzos acumulados |
| `n_cum_rappel_biv` | refuerzos bivalentes acumulados |

### Coberturas

| Campo | Significado |
|---|---|
| `couv_dose1` | porcentaje de cobertura de primera dosis |
| `couv_complet` | porcentaje con esquema inicial completo |
| `couv_rappel` | cobertura de primer refuerzo |
| `couv_2_rappel` | cobertura de segundo refuerzo |
| `couv_3_rappel` | cobertura de tercer refuerzo |
| `couv_rappel_biv` | cobertura de refuerzo bivalente |

### Sufijos de sexo del archivo de 57 columnas

| Sufijo | Significado |
|---|---|
| `_h` | hombres |
| `_f` | mujeres |
| `_e` | total de sexos, incluido no informado |

Ejemplos:

- `n_dose1_h`: primeras dosis diarias en hombres.
- `n_cum_complet_f`: mujeres acumuladas con esquema completo.
- `couv_rappel_e`: cobertura total de primer refuerzo.

### Profesionales

| Campo | Significado |
|---|---|
| `pro_couv_dose1` | cobertura de primera dosis en profesionales |
| `pro_couv_complet` | cobertura de esquema completo en profesionales |
| `pro_couv_rappel` | cobertura de primer refuerzo en profesionales |
| `pro_couv_2_rappel` | cobertura de segundo refuerzo en profesionales |
| `pro_couv_3_rappel` | cobertura de tercer refuerzo en profesionales |
| `pro_couv_rappel_biv` | cobertura de refuerzo bivalente en profesionales |

### Residentes

| Campo | Significado |
|---|---|
| `res_couv_dose1` | cobertura de primera dosis en residentes |
| `res_couv_complet` | cobertura de esquema completo en residentes |
| `res_couv_rappel` | cobertura de primer refuerzo en residentes |
| `res_couv_2_rappel` | cobertura de segundo refuerzo en residentes |

## 9. Códigos de edad

| Código | Grupo de edad |
|---|---|
| `0` | todas las edades |
| `04` | 0–4 años |
| `09` | 5–9 años |
| `11` | 10–11 años |
| `17` | 12–17 años |
| `24` | 18–24 años |
| `29` | 25–29 años |
| `39` | 30–39 años |
| `49` | 40–49 años |
| `59` | 50–59 años |
| `64` | 60–64 años |
| `69` | 65–69 años |
| `74` | 70–74 años |
| `79` | 75–79 años |
| `80` | 80 años o más |

## 10. Códigos de sexo

| Código | Categoría |
|---|---|
| `0` | total, incluido no informado |
| `1` | hombre |
| `2` | mujer |

## 11. Códigos de vacuna

| Código | Vacuna | Fabricante |
|---|---|---|
| `0` | todas las vacunas | todos |
| `1` | Comirnaty 30 adulto | Pfizer/BioNTech |
| `2` | Spikevax | Moderna |
| `3` | Vaxzevria | AstraZeneca |
| `4` | Janssen | Johnson & Johnson |
| `5` | Comirnaty 10 pediátrica | Pfizer/BioNTech |
| `6` | Nuvaxovid | Novavax |
| `8` | código presente pero no descrito en el catálogo publicado | no documentado |
| `9` | Spikevax bivalente | Moderna |
| `10` | VidPrevtyn Beta | Sanofi |
| `11` | Comirnaty 3 pediátrica, 6 meses–4 años | Pfizer/BioNTech |
| `12` | Spikevax bivalente original/Ómicron BA.5 | Moderna |

No se inventó una etiqueta para el código `8`; se conserva como no documentado porque la publicación consultada no proporciona su nombre.

## 12. Cómo interpretar correctamente los datos

- Para obtener actividad durante un mes se suman las columnas diarias `n_*`.
- Para conocer un acumulado mensual se utiliza el último valor disponible de `n_cum_*` en ese mes.
- Para conocer la cobertura mensual se utiliza el último valor disponible de `couv_*`.
- Los porcentajes de cobertura no deben sumarse.
- El grupo de edad `0` ya representa el total y no debe sumarse con los grupos detallados.
- El sexo `0` ya representa el total y no debe sumarse con hombre y mujer.
- La vacuna `0` ya representa todas las vacunas y no debe sumarse con cada producto.
- En un mapa se debe utilizar una sola fecha de corte o un solo mes.

## 13. Periodos útiles

- 2020 solo contiene los últimos días de diciembre.
- 2021 está completo.
- 2022 está completo.
- 2023 contiene datos hasta el 10 de julio.
- Para comparaciones entre años completos conviene utilizar 2021 y 2022.
- Para un mapa reciente de un mes completo conviene utilizar junio de 2023.

## 14. Información sobre profesionales y residentes

Los profesionales corresponden a personas identificadas como trabajadores de EHPAD o USLD. La fuente informa que la cohorte supera 100.000 profesionales, pero no representa a todos los trabajadores de Francia.

Los residentes corresponden a personas identificadas como residentes de EHPAD o USLD. La fuente informa que la cohorte supera 300.000 residentes y tampoco es exhaustiva.

Estos archivos no contienen nombre, profesión exacta, establecimiento o identificador personal.

## 15. Información que no contienen los datos abiertos

Los CSV descargados no contienen:

- nombre del paciente;
- documento de identidad;
- nombre del vacunador;
- profesión exacta del vacunador;
- establecimiento de aplicación;
- dirección personal;
- lote de vacuna;
- una fila individual por cada aplicación.

La información está agregada para proteger la privacidad.

## 16. Verificaciones realizadas después de la descarga

- Se comparó el tamaño descargado con el tamaño publicado por la fuente.
- Se contaron filas y columnas de cada archivo.
- Se comprobó el rango de fechas.
- Se revisó la cantidad de territorios, edades, sexos y vacunas.
- No se encontraron filas con una cantidad incorrecta de columnas.
- Se generaron hashes SHA-256 en `docs/CHECKSUMS_SHA256.txt`.

Estas verificaciones no modificaron los CSV originales.

## 17. Aclaración sobre archivos complementarios

La única fuente de datos crudos está en `data/raw`. Otras carpetas del paquete contienen documentación, nombres geográficos o archivos para mapas. Esos complementos no forman parte de los siete CSV originales y no alteran su contenido.

Para comenzar el análisis desde cero se debe trabajar primero con `data/raw` y este diccionario.

## 18. Proyecto de inteligencia de negocios

Este repositorio también contiene la base de planificación para desarrollar la **Ruta 05 — Cobertura de vacunación** del Proyecto Integrador de Visualización de Datos. La decisión propuesta es localizar brechas por grupo de edad y territorio mediante un mapa coroplético, tendencias mensuales y un tablero en Power BI.

El desarrollo usará Python y Jupyter para perfilamiento y ETL, SQL Server como plataforma de datos, Power BI para el modelo y tablero, QGIS como apoyo de control geoespacial y GitHub con Git LFS para versiones.

Documentos principales:

- [Acta de alcance](docs/ACTA_ALCANCE.md)
- [Planificación diaria de cuatro semanas](docs/PLANIFICACION_4_SEMANAS.md)
- [Arquitectura Microsoft](docs/ARQUITECTURA_MICROSOFT.md)
- [Plan de ETL y SQL Server](docs/PLAN_ETL_SQL_SERVER.md)
- [Matriz de cumplimiento del PDF](docs/MATRIZ_CUMPLIMIENTO_PDF.md)
- [Estrategia de Git y GitHub](docs/ESTRATEGIA_GIT_GITHUB.md)
- [Diccionario técnico completo](docs/DICCIONARIO_DATOS_COMPLETO.md)
- [Guía de mapas y BI](docs/GUIA_MAPAS_Y_BI.md)

La planificación empieza el 30 de octubre de 2026, dura 28 días y suma 80 horas: 2 horas como máximo de lunes a viernes y 5 horas como máximo los sábados y domingos. La documentación distingue claramente lo que ya existe de lo que todavía debe desarrollarse.
