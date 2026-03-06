# Time Series Class Materials

Repositorio para dos sesiones practicas de series temporales, con notebooks claros y autoexplicativos.

## Estructura

- `data/raw`: datos originales (no editar).
- `data/processed`: datos limpios creados en notebooks.
- `notebooks`: notebook 1 (FX no estacionaria) y notebook 2 (Metro con estacionalidad compleja).
- `reports`: carpeta para exportar graficos si se quiere.

## Datasets usados

- `data/raw/tipos_cambio.csv`
- `data/raw/demanda_diaria_metro_2015_2024.csv`

## Notebooks de clase

- `notebooks/01_intro_no_estacionaria_fx.ipynb`
- `notebooks/02_metro_estacionalidad_compleja.ipynb`

Cada notebook incluye:
- EDA rapido de dominio.
- Parseo de fechas y limpieza.
- Guardado de fichero limpio.
- Visualizacion temporal.
- Forecast con intervalos de confianza.
- Backtesting temporal.

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
