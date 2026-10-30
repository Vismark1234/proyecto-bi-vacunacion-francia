# Diccionario completo de datos

## 1. Campos dimensionales

| Campo | Definición | Tipo SQL sugerido | Observación |
|---|---|---|---|
| `dep` | código del departamento o territorio | `varchar(3)` | conservar ceros y valores `2A`, `2B` |
| `clage_vacsi` | código de grupo de edad | `varchar(2)` | `0` representa todas las edades |
| `sexe` | código de sexo | `char(1)` | `0` total, `1` hombre, `2` mujer |
| `vaccin` | código de vacuna | `varchar(2)` | `0` representa todas las vacunas |
| `jour` | fecha de observación/inyección | `date` | formato `YYYY-MM-DD` |

## 2. Convenciones de medidas

| Patrón | Significado | Unidad | Regla mensual |
|---|---|---|---|
| `n_*` | cantidad del día | personas | sumar |
| `n_cum_*` | cantidad acumulada hasta la fecha | personas | tomar último día disponible |
| `couv_*` | cobertura | porcentaje 0–100 | tomar último día disponible; no sumar |
| `pro_couv_*` | cobertura de profesionales | porcentaje 0–100 | tomar último día disponible |
| `res_couv_*` | cobertura de residentes | porcentaje 0–100 | tomar último día disponible |
| sufijo `_h` | hombres | depende de la medida | no sumar con `_e` |
| sufijo `_f` | mujeres | depende de la medida | no sumar con `_e` |
| sufijo `_e` | total de sexos | depende de la medida | usar como total oficial |

## 3. Significado de los indicadores

| Componente | Descripción |
|---|---|
| `dose1` | primera dosis |
| `dose2` | segunda dosis |
| `dose3` | tercera dosis |
| `dose4` | cuarta dosis |
| `complet` | esquema inicial de vacunación completo |
| `rappel` | al menos un refuerzo |
| `2_rappel` | segundo refuerzo |
| `3_rappel` | tercer refuerzo |
| `rappel_biv` | refuerzo bivalente adaptado a variantes |

Ejemplos:

- `n_dose1`: personas con primera dosis registrada ese día.
- `n_cum_complet`: personas acumuladas con esquema completo.
- `couv_complet`: porcentaje de cobertura de esquema completo.
- `n_rappel_biv_f`: mujeres con refuerzo bivalente registrado ese día.
- `couv_2_rappel_h`: cobertura de segundo refuerzo en hombres.

## 4. Esquema completo por archivo

### `vacsi-dep-2023-07-13-15h50.csv`

Granularidad: una fila por `dep + jour`.

```text
dep, jour,
n_dose1, n_complet, n_rappel, n_2_rappel, n_rappel_biv, n_3_rappel,
n_cum_dose1, n_cum_complet, n_cum_rappel, n_cum_2_rappel,
n_cum_rappel_biv, n_cum_3_rappel,
couv_dose1, couv_complet, couv_rappel, couv_2_rappel,
couv_rappel_biv, couv_3_rappel
```

### `vacsi-a-dep-2023-07-13-15h50.csv`

Granularidad: una fila por `dep + clage_vacsi + jour`.

Contiene las mismas 18 medidas de la tabla general, más `clage_vacsi`.

### `vacsi-s-dep-2023-07-13-15h51.csv`

Granularidad: una fila por `dep + sexe + jour`.

Contiene las mismas 18 medidas de la tabla general, más `sexe`.

### `vacsi-v-dep-2023-07-13-15h51.csv`

Granularidad: una fila por `dep + vaccin + jour`.

```text
dep, vaccin, jour,
n_dose1, n_dose2, n_dose3, n_dose4,
n_complet, n_rappel, n_2_rappel, n_rappel_biv, n_3_rappel,
n_cum_dose1, n_cum_dose2, n_cum_dose3, n_cum_dose4,
n_cum_complet, n_cum_rappel, n_cum_2_rappel,
n_cum_rappel_biv, n_cum_3_rappel
```

La tabla por vacuna no incluye coberturas; contiene cantidades diarias y acumuladas.

### `vacsi-s-a-dep-2023-07-13-15h51.csv`

Granularidad: una fila por `dep + clage_vacsi + jour`. El sexo está expresado mediante grupos de columnas.

Campos de hombres:

```text
n_dose1_h, n_complet_h, n_rappel_h, n_2_rappel_h,
n_rappel_biv_h, n_3_rappel_h,
n_cum_dose1_h, n_cum_complet_h, n_cum_rappel_h,
n_cum_2_rappel_h, n_cum_rappel_biv_h, n_cum_3_rappel_h,
couv_dose1_h, couv_complet_h, couv_rappel_h,
couv_2_rappel_h, couv_rappel_biv_h, couv_3_rappel_h
```

Campos de mujeres: los mismos nombres sustituyendo `_h` por `_f`.

Campos totales: los mismos nombres sustituyendo `_h` por `_e`.

La tabla contiene 3 campos dimensionales más 18 medidas × 3 grupos de sexo = 57 columnas.

### `vacsi-prof-dep-2023-07-13-15h51.csv`

Granularidad: una fila por `dep + jour`.

```text
dep, jour,
pro_couv_dose1, pro_couv_complet, pro_couv_rappel,
pro_couv_2_rappel, pro_couv_rappel_biv, pro_couv_3_rappel
```

### `vacsi-resid-dep-2023-07-13-15h51.csv`

Granularidad: una fila por `dep + jour`.

```text
dep, jour,
res_couv_dose1, res_couv_complet,
res_couv_rappel, res_couv_2_rappel
```

## 5. Grupos de edad

| Código | Grupo |
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

## 6. Vacunas

| Código | Vacuna | Fabricante |
|---|---|---|
| `0` | todas las vacunas | todos |
| `1` | Comirnaty 30 adulto | Pfizer/BioNTech |
| `2` | Spikevax | Moderna |
| `3` | Vaxzevria | AstraZeneca |
| `4` | Janssen | Johnson & Johnson |
| `5` | Comirnaty 10 pediátrica | Pfizer/BioNTech |
| `6` | Nuvaxovid | Novavax |
| `8` | código presente, etiqueta no descrita en el catálogo publicado | no documentado |
| `9` | Spikevax bivalente | Moderna |
| `10` | VidPrevtyn Beta | Sanofi |
| `11` | Comirnaty 3 pediátrica, 6 meses–4 años | Pfizer/BioNTech |
| `12` | Spikevax bivalente original/Ómicron BA.5 | Moderna |

No se asignó una etiqueta inventada al código `8`; se conserva explícitamente como no documentado.

## 7. Claves y relaciones

| Hecho | Clave lógica |
|---|---|
| general | `dep + jour` |
| edad | `dep + clage_vacsi + jour` |
| sexo | `dep + sexe + jour` |
| vacuna | `dep + vaccin + jour` |
| edad-sexo | `dep + clage_vacsi + jour` |
| profesionales | `dep + jour` |
| residentes | `dep + jour` |

Relaciones de dimensiones:

```text
dep           -> DimDepartamento[dep]
jour          -> DimFecha[fecha]
clage_vacsi   -> DimGrupoEdad[clage_vacsi]
sexe          -> DimSexo[sexe]
vaccin        -> DimVacuna[vaccin]
```

## 8. Reglas para evitar errores

1. Importar los códigos como texto.
2. No sumar el grupo de edad `0` con grupos detallados.
3. No sumar sexo `0` con hombre y mujer.
4. No sumar vacuna `0` con vacunas específicas.
5. Sumar `n_*` para obtener actividad mensual.
6. Usar el último `n_cum_*` para un acumulado mensual.
7. Usar el último `couv_*` para cobertura mensual.
8. No sumar ni promediar coberturas sin ponderación poblacional.
9. Filtrar una única fecha de corte para el mapa.
10. Tratar 2020 y 2023 como años parciales.

## 9. Tipos SQL recomendados

| Familia | Tipo SQL |
|---|---|
| códigos | `varchar` |
| fecha | `date` |
| cantidades | `bigint` |
| coberturas | `decimal(9,4)` |
| nombres/descripciones | `nvarchar` |

## 10. Limitaciones semánticas

- Los datos son agregados, no registros individuales.
- No hay nombres de pacientes, trabajadores o vacunadores.
- No hay establecimiento, lote ni inventario.
- Profesionales y residentes son cohortes específicas EHPAD/USLD.
- La publicación terminó en julio de 2023.
- La tabla de vacuna mide cantidades, no cobertura por producto.

