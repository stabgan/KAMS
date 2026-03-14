# KAMS — Knowledge-based Agricultural Modeling System

Exploratory data analysis and machine learning experiments for predicting evapotranspiration and analyzing rice production trends in Egypt, developed as a final-year research project.

## What It Does

This project contains three Jupyter notebooks that together form a pipeline for agricultural climate analysis:

1. **Weather Analysis** (`weather_egypt.ipynb`) — Loads daily weather observations for Egypt (temperature, wind speed, vapour pressure, precipitation, radiation, etc.), drops irrelevant columns, and trains a **Random Forest Regressor** to predict evapotranspiration (ET0) from the remaining climate features. Achieves an R² score of ~0.9999 on the test set.

2. **Preprocessing & Geospatial Filtering** (`Preprocessing_Weather.ipynb`) — Reads a larger weather dataset covering 655 grid locations across Egypt, extracts unique lat/lon pairs, and uses **Shapely** polygon containment tests to identify which weather stations fall within Egypt's key agricultural (cropland) regions. Also loads and reshapes historical rice production statistics.

3. **Rice Production Trends** (`Copy of egypt1.ipynb`) — Visualizes historical trends (1961–2014) for paddy production, rice cultivation area, and fertilizer usage in Egypt using **Matplotlib**.

## Dataset

The notebooks expect the following data files in the project root (not included in this repository):

| File | Description |
|------|-------------|
| `weather.csv` | Daily weather observations (semicolon-separated) |
| `egypt1975.csv` | Extended weather dataset with 655 grid locations |
| `rice1.csv` | Historical rice production statistics (1961–2014) |
| `egypt1.csv` | Transposed rice/agriculture statistics |
| `export.xls` | Crop calendar data |

## 🛠 Tech Stack

| | Technology | Purpose |
|---|-----------|---------|
| 🐍 | Python 3 | Core language |
| 🐼 | pandas | Data loading, manipulation, and preprocessing |
| 🔢 | NumPy | Numerical operations |
| 📊 | Matplotlib | Data visualization and trend plotting |
| 🌍 | Shapely | Geospatial polygon containment tests |
| 🤖 | scikit-learn | Random Forest Regression, train/test split, R² scoring |

## Installation

```bash
pip install numpy pandas matplotlib shapely scikit-learn openpyxl
```

## Usage

1. Place the required CSV/XLS data files in the project root.
2. Launch Jupyter:
   ```bash
   jupyter notebook
   ```
3. Open and run the notebooks in order:
   - `weather_egypt.ipynb`
   - `Preprocessing_Weather.ipynb`
   - `Copy of egypt1.ipynb`

## ⚠️ Known Issues

- **Missing data files** — The CSV and XLS datasets referenced by the notebooks are not included in this repository. You will need to source them independently.
- **Hardcoded file paths** — All notebooks use relative paths assuming data files are in the same directory.
- **NaN handling** — The rice production dataset contains missing values (NaN) for some years/metrics. The plotting code now converts these to `0.0`, which may not be ideal for all analyses.
