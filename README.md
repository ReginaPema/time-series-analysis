# <img src="https://img.icons8.com/?size=50&id=81302&format=png&color=000000" align="center"/> Time Series Analysis
### Análisis de Series de Tiempo: EDA · AR · ARIMA

> **EN** · Three notebooks covering the foundational time series pipeline: exploratory analysis and decomposition, auto-regressive AR(p) modeling, and full ARIMA(p,d,q) estimation via the Box-Jenkins methodology. All data downloads automatically; no local files required.
>
> **ES** · Tres notebooks que cubren el flujo base de series de tiempo: análisis exploratorio y descomposición, modelado auto-regresivo AR(p), y estimación ARIMA(p,d,q) completa por la metodología Box-Jenkins. Todos los datos se descargan automáticamente, no se requieren archivos locales.

---

## <img src="https://img.icons8.com/?size=40&id=80454&format=png&color=000000" align="center"/> Notebooks

### 01 · EDA: IBM vs Walmart Stock Prices (5 years)
**Data:** Yahoo Finance via `yfinance`; 5 years daily prices, ~1,250 observations per ticker

- Downloaded and explored 5 years of daily closing prices for IBM and Walmart
- Applied **STL decomposition** to separate trend, seasonality and residual components
- Computed **ACF and PACF** correlograms to characterize autocorrelation structure
- **Dickey-Fuller stationarity test** on both series
- Built **SMA-5 and SMA-20** moving average forecasts
- **Critical evaluation:** SMA achieves MAPE of 1.97% (IBM) and 1.51% (WMT), but this is a statistical illusion: moving averages track yesterday's price, not true future behavior (random walk effect)

---

### 02 · AR(p) Model: Disney (DIS) Stock Price
**Data:** Yahoo Finance via `yfinance`; DIS daily prices Jan–Apr 2023

- Selected optimal AR order using **PACF cutoff** and **AIC/BIC** grid comparison
- **Optimal model: AR(1)**; PACF drops off after lag 1
- Train/test split: 70% (Jan–Mar 2023) for estimation, 30% for in-sample validation
- **Out-of-sample forecast for April 2023** compared against real observed prices
- AR(1) outperforms naive **Random Walk benchmark**: RMSE **4.853** vs 5.383 USD

---

### 03 · ARIMA(p,d,q): New York Annual Temperature (1870–2020)
**Data:** Public CSV; 151 annual temperature observations, auto-downloaded from GitHub

- Full **Box-Jenkins methodology** applied to 150 years of climate data
- **Stationarity:** series non-stationary in level (ADF p>0.05) → stationary after d=1
- **Grid search:** 16 ARIMA(p,d,q) combinations ranked by AIC → **ARIMA(3,1,3) selected**
- **Residual diagnostics:** Ljung-Box (white noise), normality, ACF of residuals
- **Stationarity and invertibility** of fitted AR and MA polynomials verified via `ArmaProcess`
- Forecast with **confidence intervals**; MAPE < 3% on test set

---

## <img src="https://img.icons8.com/?size=40&id=80717&format=png&color=000000" align="center"/> Models Summary / Resumen de Modelos

| Notebook | Asset / Serie | Method | Key Result |
|---|---|---|---|
| 01 | IBM · WMT | SMA-5 · SMA-20 | MAPE 1.97%/1.51%; deceptively low (random walk) |
| 02 | DIS | AR(1) | RMSE 4.853 vs 5.383 (random walk benchmark) |
| 03 | NYC Temperature | ARIMA(3,1,3) | MAPE < 3% · d=1 · AIC grid search 16 candidates |

---

## <img src="https://img.icons8.com/?size=40&id=80431&format=png&color=000000" align="center"/> Tools / Herramientas

![Python](https://img.shields.io/badge/Python-8B9E8B?style=flat&logo=python&logoColor=white)
![yfinance](https://img.shields.io/badge/yfinance-3D6B4F?style=flat)
![Statsmodels](https://img.shields.io/badge/Statsmodels-4B6CB7?style=flat)
![Pandas](https://img.shields.io/badge/Pandas-6B7F6B?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-7A9E9F?style=flat&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat)
![Jupyter](https://img.shields.io/badge/Jupyter-C4A882?style=flat&logo=jupyter&logoColor=white)

---

## <img src="https://img.icons8.com/?size=40&id=80358&format=png&color=000000" align="center"/> Related Project / Proyecto Relacionado

> For an applied forecasting project, ARIMA/SARIMA vs linear regression benchmark on real retail sales data, see:

| Project | Description |
|---|---|
| [ARIMA-SARIMA_sales_forecast](https://github.com/ReginaPema/ARIMA-SARIMA_sales_forecast) | Box-Jenkins models vs MLR benchmark for weekly retail sales forecasting |

---

## <img src="https://img.icons8.com/?size=40&id=PhymLYNNjf3I&format=png&color=000000" align="center"/> Repository Structure / Estructura

```
time-series-analysis/
├── notebooks/
│   ├── 01_eda_time_series_ibm_walmart.ipynb
│   ├── 02_ar_model_disney_stock.ipynb
│   └── 03_arima_nyc_temperature.ipynb
└── README.md
```

> All datasets download automatically when the notebooks run:
> - Notebooks 01 & 02: `yfinance` pulls from Yahoo Finance
> - Notebook 03: CSV loaded from a public GitHub URL
>
> No local data files required / No se requieren archivos de datos locales.

---

*Project developed as part of the Data Scientist Certificate · 
Proyecto desarrollado como parte del certificado Científico de Datos — EBAC (2026)* <img src="https://img.icons8.com/?size=35&id=FgMs84V9yrMV&format=png&color=000000" align="center"/>
