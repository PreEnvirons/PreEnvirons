# Datos del seminario *Disease mapping*

> ⚠️ **Los datos de salud son SINTÉTICOS.** No contienen información de personas reales.
> Las covariables socioeconómicas y la geometría **sí** son reales (fuentes públicas).

## `palma_secciones.geojson`

Una fila por **sección censal** del municipio de Palma (CRS WGS84 / EPSG:4326).

| Campo      | Descripción                                                        | Fuente                         |
|------------|--------------------------------------------------------------------|--------------------------------|
| `CUSEC`    | Código de sección censal (10 dígitos, texto)                        | INE / SEE                      |
| `NMUN`     | Municipio (Palma)                                                   | INE                            |
| `ip_see`   | Índice de privación (alto = más desfavorecido)                      | **Real** — SEE, IP2011         |
| `renta`    | Renta neta media por persona (€)                                    | **Real** — INE ADRH, 2022      |
| `quintil`  | Quintil de privación (1 = menos, 5 = más desfavorecido)             | Derivado de `ip_see`           |

245 secciones.

## `obesidad_infantil_palma_sintetica.csv`

Una fila por **sección × sexo × grupo de edad** (formato largo).

| Campo        | Descripción                                              |
|--------------|---------------------------------------------------------|
| `CUSEC`      | Código de sección censal (texto)                        |
| `sexo`       | `Niño` / `Niña`                                         |
| `grupo_edad` | `2-5`, `6-11`, `12-15`                                  |
| `poblacion`  | Nº de menores en ese estrato (sintético)               |
| `casos`      | Nº con obesidad en ese estrato (sintético)             |

1.470 filas (245 secciones × 2 sexos × 3 grupos de edad).

## ¿Cómo se generaron los casos sintéticos?

1. Prevalencia base de obesidad por sexo y edad (criterio **OMS**: z-score de IMC), calibrada con las cifras del estudio real de obesidad infantil en áreas pequeñas de Baleares (Programa de Salut Infantoadolescent).
2. Multiplicada por el **riesgo relativo por quintil de privación** estimado en el modelo espacial **BYM** real del grupo (RIE Q5/Q1 ≈ 1,4).
3. Recuentos generados con una distribución binomial (semilla `1854`, el año del mapa de cólera de John Snow).

El resultado reproduce el **gradiente socioeconómico real** sin usar ningún microdato sanitario.
