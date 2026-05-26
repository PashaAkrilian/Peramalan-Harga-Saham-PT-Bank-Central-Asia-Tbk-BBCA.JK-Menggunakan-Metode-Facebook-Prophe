# Forecasting BBCA.JK Stock Prices Using Facebook Prophet

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Method](https://img.shields.io/badge/Method-Facebook%20Prophet-green.svg)
![Task](https://img.shields.io/badge/Task-Time%20Series%20Forecasting-red.svg)

A financial time series forecasting project focused on predicting the daily closing prices of **PT Bank Central Asia Tbk (BBCA.JK)** using the **Facebook Prophet** forecasting framework.

This study evaluates the ability of Prophet to model:
- non-linear financial trends
- seasonal behavior
- non-stationary stock data
- short-term future price movements

The model achieved highly robust forecasting performance with:

- **MAE : 582.6611**
- **RMSE : 598.0191**
- **MAPE : 0.0970**

based on out-of-sample evaluation.

---

# Project Overview

Stock prices are highly dynamic and influenced by:
- macroeconomic conditions
- monetary policy
- market sentiment
- company fundamentals
- investor psychology

Because of these characteristics, financial data often exhibit:
- non-stationarity
- long-term stochastic trends
- nonlinear movement
- seasonal structures
- irregular volatility

This project applies the **Facebook Prophet** additive forecasting framework to capture these complex temporal patterns in BBCA.JK stock prices.

---

# Repository Structure

```bash
Forecasting-BBCA-Prophet/
│
├── 2404220026_Dimas_Pasha_Akrilian_Project_ARW_Revisi.pdf
├── prophet_forecasting_bbca.ipynb
├── outputs/
│   ├── forecast_plot.png
│   ├── prediction_interval.png
│   └── evaluation_metrics.csv
├── LICENSE
└── README.md
```

---

# Workflow

```text
Load BBCA.JK stock data
        ↓
Data preprocessing
        ↓
Missing value handling
        ↓
ADF stationarity testing
        ↓
Facebook Prophet modeling
        ↓
Trend & seasonality decomposition
        ↓
Model training
        ↓
5-period forecasting
        ↓
Performance evaluation
        ↓
Visualization & interpretation
```

---

# Dataset Information

The dataset contains:

```text
1,787 daily observations
```

covering the period:

```text
January 1, 2019 → May 8, 2026
```

The data source used in the study is:

```text
Yahoo Finance
```

The primary target variable is:

```text
Daily Closing Price of BBCA.JK
```

---

# Methodology

# 1. Data Preprocessing

Financial time series frequently contain:
- missing observations
- irregular trading intervals
- zero-volume anomalies

To maintain structural consistency, the study applies:

## Forward Fill

```text
ffill()
```

for propagating previous valid observations.

## Backward Fill

```text
bfill()
```

for handling remaining boundary missing values.

---

# 2. Stationarity Testing

The project applies:

```text
Augmented Dickey-Fuller (ADF) Test
```

to determine whether the stock price series contains a unit root.

## Hypothesis

### Null Hypothesis

```text
Series is non-stationary
```

### Alternative Hypothesis

```text
Series is stationary
```

The empirical result:

```text
ADF Statistic = -1.7121
p-value = 0.4249
```

Since:

```text
p-value > 0.05
```

the series is confirmed to be non-stationary.

---

# 3. Facebook Prophet Model

The forecasting framework used is:

```text
Facebook Prophet
```

Prophet models time series as:

```text
y(t)=g(t)+s(t)+h(t)+εt
```

where:

- g(t) → trend component
- s(t) → seasonality
- h(t) → holiday effects
- εt → error term

The model is especially effective for:
- non-linear trends
- multiple seasonalities
- missing data handling
- automatic changepoint detection

---

# 4. Trend Modeling

The long-term trend is modeled using a piecewise linear growth structure:

```text
g(t)=(k+a(t)^Tδ)t+(m+a(t)^Tγ)
```

This formulation allows Prophet to automatically adapt to structural changes in stock price behavior.

---

# 5. Seasonality Modeling

Seasonality is approximated using Fourier series:

```text
s(t)=Σ(Aₙcos(2πnt/P)+Bₙsin(2πnt/P))
```

This enables the model to capture:
- weekly trading cycles
- annual market behavior
- recurring temporal structures

---

# 6. Model Evaluation

The forecasting model is evaluated using:

## Mean Absolute Error (MAE)

```text
MAE = (1/n) Σ |yi - ŷi|
```

## Mean Squared Error (MSE)

```text
MSE = (1/n) Σ (yi - ŷi)²
```

## Mean Absolute Percentage Error (MAPE)

```text
MAPE = (1/n) Σ |(yi - ŷi)/yi| × 100%
```

---

# Empirical Results

## Forecasting Performance

| Metric | Value |
|---|---|
| MAE | 582.6611 |
| RMSE | 598.0191 |
| MAPE | 0.0970 |

The low MAPE value demonstrates that the Prophet framework successfully captures the directional movement of BBCA stock prices with strong short-term predictive precision.

---

# Key Findings

The study concludes that:

- Prophet effectively handles non-stationary financial series
- nonlinear trends are captured successfully
- seasonal structures are modeled automatically
- forecasting intervals remain stable
- short-term predictions are highly reliable

The results validate Prophet as a practical forecasting framework for Indonesian equity market analysis.

---

# Example Usage

```python
from prophet import Prophet
import pandas as pd

df = pd.read_csv("bbca_stock.csv")

model = Prophet()
model.fit(df)

future = model.make_future_dataframe(periods=5)
forecast = model.predict(future)

print(forecast[['ds', 'yhat']].tail())
```

---

# Tech Stack

- Python
- pandas
- NumPy
- matplotlib
- statsmodels
- prophet
- scikit-learn

---

# Use Cases

This project is highly relevant for:

- stock price forecasting
- financial econometrics
- investment analysis
- algorithmic trading research
- Indonesian capital market studies
- time series forecasting coursework

---

# License

This project is licensed under the **MIT License**.

You are free to use, modify, distribute, and adapt this work with proper attribution.

---

# MIT License

Copyright (c) 2026 Dimas Pasha Akrilian

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

# Author

**Dimas Pasha Akrilian**

This repository is part of my financial time series and forecasting portfolio, focusing on:

- stock market forecasting
- Prophet-based forecasting systems
- financial econometrics
- statistical time series analysis
- machine learning for finance
