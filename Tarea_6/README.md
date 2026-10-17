# Tarea 6 — Integración final de datos históricos del Tour de Francia

## Descripción

Proyecto de limpieza, integración y análisis de datos históricos del Tour de Francia utilizando Python, Pandas y Jupyter Notebook.

## Fuente de los datos

Repositorio [LeTourDataSet](https://github.com/thomascamminady/LeTourDataSet), de Thomas Camminady.

Se utilizaron cuatro archivos CSV de resultados históricos masculinos y femeninos. El análisis principal se realizó con las tablas masculinas.

## Archivos del proyecto

| Archivo o carpeta | Descripción |
|---|---|
| `Unidad2_Tarea6_Integracion_Final.ipynb` | Notebook con diagnóstico, limpieza, integración, análisis y validaciones. |
| `datos_tarea6/` | Cuatro archivos CSV originales. |
| `resultados_tarea6/tour_ciclistas_integrados.parquet` | Dataset final limpio e integrado. |

## Problemas detectados y transformaciones

Se identificaron valores faltantes en columnas históricas de clasificación y 271 registros cuyos valores de `TotalSeconds` y `GapSeconds` eran cero en categorías no basadas en tiempo.

Estos valores se reemplazaron por `pd.NA`, conservando los registros y los ceros válidos. No se imputaron resultados históricos sin evidencia.

Posteriormente, se agruparon las etapas por año y se integraron con los datos de ciclistas mediante `merge()`, verificando la relación `many_to_one`.

## Resultados

El dataset integrado contiene **10,337 registros y 17 columnas**, sin duplicados exactos.

Se generaron resúmenes anuales mediante `groupby()` y una tabla dinámica con `pivot_table()`. La integridad de los resultados se verificó mediante comprobaciones automáticas y una lectura posterior del archivo Parquet.

## Reproducibilidad

Para reproducir el análisis:

1. Descargar el repositorio.
2. Instalar Python y las dependencias `pandas`, `requests` y `pyarrow`, según corresponda al entorno.
3. Abrir `Unidad2_Tarea6_Integracion_Final.ipynb` en Jupyter o PyCharm.
4. Ejecutar todas las celdas en orden, desde la carpeta `Tarea_6`.

## Limitaciones

Los datos presentan diferencias de cobertura entre periodos históricos y valores faltantes en algunas clasificaciones. Los resultados dependen de la información disponible en la fuente y no necesariamente representan la totalidad de participantes oficiales. Las comparaciones entre ediciones pueden estar afectadas por cambios de recorridos, distancias y modalidades de clasificación.

La licencia y las condiciones de reutilización de los datos deben verificarse en la fuente original.
