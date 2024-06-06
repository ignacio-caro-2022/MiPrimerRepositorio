# Ejercicio Ecobicis

El objetivo de este ejercicio es desarrollar un modelo de predicción de demanda de viajes en bicicleta para las estaciones de Ecobici usando datos de 2022.

## Cómo ejecutar el análisis
### Estructura de carpetas

### Scripts
| Script | Descripción |
| ----------------- | ----------------------- |
| `data_prep.py` | A partir del conjunto de datos original ("trips_2022.csv") construye el input del modelo: agrega los datos originales (a nivel viaje) al nivel cuadrante-día y genera los distintos features |
| `eda.py` | A partir del input transformado (output de `data_prep.py`) ejecuta el análisis exploratorio: tanto univariado como bivariado, en gráficos y tablas |
| `modelo_regresion.py` | Contiene una función que entrena modelos de regresión lineal, usando _Secuential Feature Selection_ para seleccionar las variables |
| `modelo_lightgbm.py` | Contiene una función que entrena modelos de regresión con LightGBM |


## Insights

## Metodología

| Grupo de features | Feature | Descripción |
| ----------------- | ----------------------- | ----------- |
| Calendario | `dayofmonth` | Día del mes (1-31) |
| Calendario | `dayofyear` | Día del año (1-365) |
| Calendario | `monthofyear` | Mes del año (1-12) |
| Calendario | `quarterofyear` | Trimestre del año (1-4) |
| Calendario | `dayofweek` | Día de la semana, 1 = lunes (1-7) |
| Calendario | `halfofyear` | Semestre del año |
| Calendario | `estacionalidad_trig` | Estacionalidad trigonométrica (ver apéndice) |
| Actividad | `dialaboral` | Flag = 1 para días de semana no feriados |
| Actividad | `feriado` | Flag = 1 para feriados |
| Actividad | `findesemana` | Flag = 1 para fines de semana |
| Clima | `tavg` | Temperatura promedio observada en el día, en la estación Aeroparque, en °C (fuente: Meteostat) |
| Clima | `tmin` | Temperatura mínima observada en el día, en la estación Aeroparque, en °C (fuente: Meteostat) |
| Clima | `tmax` | Temperatura máxima observada en el día, en la estación Aeroparque, en °C (fuente: Meteostat) |
| Clima | `amplitude` | Amplitud térmica, diferencia entre la temperatura máxima y mínima |
| Clima | `flag_prcp` | Flag = 1 para días con precipitación igual o mayor a 5mm |

## Apéndice
### Estacionalidad trigonométrica

Se construyó una variable que busca capturar el patrón estacional en la demanda a partir de una función trigonométrica que tiene dos ciclos completos durante un año, con picos a mitad de cada semestre (comienzos de abril y octubre, aproximadamente).

$$ \textrm{estacionalidad trig}_t = \sin(\tfrac{4}{\pi}) $$

### Referencias
Paper
