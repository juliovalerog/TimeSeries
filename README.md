# Time Series Class Materials

Material de clase para sesiones practicas de series temporales orientadas a trabajo real de data science: diagnostico, modelado, validacion temporal, incertidumbre y toma de decision.

## Estado actual del proyecto

El repositorio queda organizado en tres notebooks con niveles distintos de ambicion metodologica:

- `notebooks/01_intro_no_estacionaria_fx.ipynb`
  - Serie financiera USD/EUR no estacionaria.
  - Flujo: limpieza -> EDA -> baseline vs ARIMA -> backtesting rolling -> interpretacion.
  - Objetivo docente: introducir validacion temporal, comparacion contra baseline y lectura basica de intervalos.

- `notebooks/02_metro_estacionalidad_compleja.ipynb`
  - Demanda diaria Metro Madrid con estacionalidad compleja.
  - Flujo: limpieza -> EDA -> descomposicion base -> refinamiento multiestacional -> comparativa de modelos.
  - Objetivo docente: mostrar como iterar desde una primera descomposicion hasta un analisis mas rico con varios enfoques.

- `notebooks/03_metro_modelo_custom_short_term.ipynb`
  - Complemento adicional fuera de clase.
  - No esta pensado como material central de la sesion, sino como ejemplo de un **modelo finalista realista** que podria construir un data scientist profesional para este caso de uso.
  - Sustituye la comparativa de muchos modelos por un **unico pipeline final** de forecasting diario a 30 dias:
    - etapa 1 determinista en `log1p(y)` con calendario rico, festivos reales, puentes, Semana Santa, Fourier anual y regimen COVID/post-COVID,
    - etapa 2 residual con boosting temporal directo multi-horizonte,
    - intervalos al 95% con cuantiles y calibracion conformal temporal,
    - rolling-origin backtesting serio sobre 2024.
  - Objetivo docente avanzado: que el alumno vea como se pasa de un notebook exploratorio/comparativo a una solucion unica, defendible y mas profesional.

## Novedades de esta version

- Se ha anadido el notebook 3 como extension avanzada del caso Metro Madrid.
- Se han reforzado los comentarios dentro del codigo de los tres notebooks para mejorar la legibilidad para alumnos.
- Se ha actualizado `requirements.txt` para incluir `holidays`, necesario para festivos reales en el notebook 3.
- Se incluye una salida de forecast final:
  - `outputs/metro_custom_short_term_forecast.csv`

## Como leer los notebooks

Secuencia recomendada:

1. Empezar por `01_intro_no_estacionaria_fx.ipynb` para fijar conceptos basicos.
2. Continuar con `02_metro_estacionalidad_compleja.ipynb` para trabajar estacionalidad, descomposicion y comparativas.
3. Revisar `03_metro_modelo_custom_short_term.ipynb` como material complementario avanzado.

La idea pedagogica es que el notebook 3 no sustituye la clase. La complementa mostrando como seria una version mas cercana a produccion:

- menos benchmarking y mas decision metodologica,
- mas cuidado con leakage temporal,
- mas trabajo explicito sobre la parte determinista,
- y una validacion probabilistica mas seria.

## Estructura del repo

- `data/raw`: datos originales.
- `data/processed`: datasets limpios generados por los notebooks.
- `notebooks`: cuadernos de clase y complemento avanzado.
- `outputs`: salidas exportadas del forecast final del notebook 3.
- `requirements.txt`: dependencias del entorno.

## Datasets

- `data/raw/tipos_cambio.csv`
- `data/raw/demanda_diaria_metro_2015_2024.csv`

Archivos procesados generados:

- `data/processed/fx_usd_eur_clean.csv`
- `data/processed/metro_daily_clean.csv`

Archivos de salida generados:

- `outputs/metro_custom_short_term_forecast.csv`

## Que aprende el alumno

- Como formular un analisis temporal desde problema de negocio.
- Como evaluar calidad de dato temporal antes de modelar.
- Como comparar modelos con metrica puntual y calibracion de incertidumbre.
- Como refinar una descomposicion y separar parte explicable vs parte residual.
- Como pasar de un notebook comparativo a un pipeline unico mas cercano a un entorno profesional.
- Como documentar supuestos, limitaciones y riesgos de leakage temporal.

## Ejecucion recomendada

1. Ejecutar el notebook 1 completo.
2. Ejecutar el notebook 2 completo.
3. Revisar el notebook 3 como extension avanzada y comparar su planteamiento con el del notebook 2.
4. Fijarse en las tablas y graficas de validacion, especialmente en cobertura de intervalos y error por horizonte.

## Entorno minimo

```bash
python -m venv .venv
```

En Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
jupyter notebook
```
