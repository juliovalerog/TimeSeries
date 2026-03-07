# Time Series Class Materials

Material de clase para dos sesiones practicas de series temporales orientadas a trabajo real de data science: diagnostico, modelado, validacion temporal, incertidumbre y toma de decision.

## Estado actual del proyecto

El repositorio esta listo para clase con dos notebooks autocontenidos y consistentes:

- `notebooks/01_intro_no_estacionaria_fx.ipynb`
  - Serie financiera USD/EUR no estacionaria.
  - Flujo: limpieza -> EDA -> baseline vs ARIMA -> backtesting rolling -> cierre metodologico.
  - Enfasis: precision vs riesgo, lectura de IC95, limitaciones y decisiones practicas.

- `notebooks/02_metro_estacionalidad_compleja.ipynb`
  - Demanda diaria Metro Madrid con estacionalidad compleja.
  - Flujo: limpieza -> EDA -> descomposicion base -> refinamiento de descomposicion -> comparativa de modelos.
  - Incluye comparativa mensual con 4 enfoques:
    - SARIMA
    - ETS
    - Prophet
    - Decomposition-based forecast (a partir de componentes refinadas)
  - Incluye graficas con intervalos de confianza y cierre de limitaciones/metodologia.

## Estructura del repo

- `data/raw`: datos originales (no editar).
- `data/processed`: datasets limpios generados por notebooks.
- `notebooks`: sesiones de clase.
- `requirements.txt`: dependencias para ejecutar los notebooks.

## Datasets

- `data/raw/tipos_cambio.csv`
- `data/raw/demanda_diaria_metro_2015_2024.csv`

Archivos procesados generados:
- `data/processed/fx_usd_eur_clean.csv`
- `data/processed/metro_daily_clean.csv`

## Que aprende el alumno

- Como formular un analisis temporal desde problema de negocio.
- Como evaluar calidad de dato temporal antes de modelar.
- Como comparar modelos con metrica puntual y calibracion de incertidumbre.
- Como detectar fallos del modelo y refinar (iteracion diagnostico -> mejora).
- Como documentar supuestos y limitaciones para uso responsable.

## Ejecucion recomendada

1. Ejecutar notebook 1 completo.
2. Ejecutar notebook 2 completo.
3. Revisar tablas y graficas de comparacion de modelos (MAE, RMSE, Cobertura IC95, % fuera IC95).
4. Usar el bloque de cierre de cada sesion como resumen metodologico.

## Entorno minimo (venv)

```bash
python -m venv .venv
```

En Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
jupyter notebook
```
