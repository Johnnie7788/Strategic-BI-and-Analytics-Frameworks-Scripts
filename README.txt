

# Energy Grid Forecasting – Code Challenge Solution

## Overview

This repository contains the solution to a time series forecasting code challenge. The objective is to forecast the electrical current (`current_A`) in an energy grid 24 hours ahead using hourly meteorological data (temperature, wind speed, and solar radiation). The dataset provided is synthetic and designed to simulate realistic energy grid conditions.

---

## Repository Structure

```
.
├── README.md                          # Challenge details and instructions.
├── data/
│   └── synthetic_energy_grid_data.csv  # Provided dataset
├── notebooks/
│   ├── model_development.ipynb        # Data analysis and training using Jupyter Notebook
│   └── model_inference.ipynb          # 24-hour forecasting using Jupyter Notebook
├── models/
│   └── gradient_boosting_model.pkl    # Trained Gradient Boosting model
├── forecast_results.csv               # Output from the inference notebook
├── requirements.txt                   # Python dependencies
└── (Optional) start_jupyter.sh        # Provided for Docker setups (not used — this project was built using Jupyter Notebook)
```

---

## Problem Statement

The task is to develop a forecasting model that predicts `current_A` for the next 24 hours using historical and external meteorological variables. The time resolution of the dataset is 1 hour, covering a full year.

---

## Solution Summary

- **Data Exploration & Preprocessing**:
  - Inspected distributions, outliers, and missing data
  - Verified time-series stationarity using the Augmented Dickey-Fuller test
  - Engineered lag and rolling features to capture temporal dynamics

- **Feature Engineering**:
  - Key features: `lag_24`, `rolling_mean_6`, `rolling_std_6`, `hour`
  - These capture historical trends, variability, and daily cycles

- **Model Development**:
  - Evaluated Gradient Boosting, ARIMA, and LSTM
  - Gradient Boosting Regressor selected based on lowest MAE (0.69 A) and RMSE (1.03 A)

- **Model Saving**:
  - The final trained model is saved in the `models/` directory

- **Model Inference**:
  - The 24-hour forecast is generated recursively and visualized
  - Forecasted values are saved in `forecast_results.csv`

---

## How to Run

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Run notebooks

1. Launch Jupyter Notebook:
```bash
jupyter notebook
```

2. Open and run:
   - `notebooks/model_development.ipynb` – for data analysis and training
   - `notebooks/model_inference.ipynb` – for generating the forecast

---

## Future Improvements

- Hyperparameter tuning to boost predictive accuracy
- Validation with real-world energy consumption datasets
- Testing deep learning models (e.g., optimized LSTM, Transformer)
- Estimating prediction uncertainty using probabilistic approaches
- Deployment via API for real-time forecasting

---

## Author

Submitted by **John Johnson Ogbidi**  
Email: johnjohnsonogbidi@gmail.com  
Based in Cologne, Germany

This project was completed using Python and Jupyter Notebook.
