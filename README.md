# PM2.5 Prediction Analysis Project

## Overview

This project focuses on predicting PM2.5 levels in Beijing using machine learning models. It analyzes historical air quality and meteorological data to forecast PM2.5 concentrations, aiming to aid in air quality management and public health initiatives.

## Project Structure

```
.
├── data/
│   ├── beijing_pm_25.csv
├── notebooks/
│   ├── main.ipynb
├── src/
│   ├── preprocess_data.py
│   ├── feature_engineering.py
│   ├── model_training.py
│   └── main.py
├── Dockerfile
├── requirements.txt
├── README.md
```

- `data/`: Contains the dataset used for analysis.
- `notebooks/`: Jupyter notebook with all code.
- `src/`: Source code for data processing, feature engineering, and model training.
- `Dockerfile`: Instructions for building the Docker container.
- `requirements.txt`: List of Python dependencies.

## Setup

### Prerequisites

- Docker and Git installed

### Installation

1. Clone this repository:
   ```
   git clone [Your Repository URL]
   cd [Your Repository Name]
   ```

2. Build the Docker image:
   ```
   docker build -t pm25-prediction -f Dockerfile .
   ```

3. Run the Docker container:
   ```
   docker run -p 8888:8888 pm25-prediction
   ```

4. Open the Jupyter notebook URL provided in the console output in your web browser.

## Usage

### Jupyter Notebook

Once you have the Jupyter interface open in your browser:

1. Open `task2.ipynb`.
2. Run all the notebook cells to perform data analysis, feature engineering, model training, and evaluation.

## Data

The dataset used in this project is the "Beijing PM2.5" dataset. It contains the following features:

- Temporal Information: Year, Month, Day, Hour
- Target Variable: PM2.5 concentration (μg/m³)
- Meteorological Factors: 
  - DEWP: Dew Point (°C)
  - TEMP: Temperature (°C)
  - PRES: Pressure (hPa)
  - cbwd: Combined wind direction
  - Iws: Cumulated wind speed (m/s)
- Precipitation Indicators:
  - Is: Cumulated hours of snow
  - Ir: Cumulated hours of rain

## Models

The project evaluates several machine learning models:

- XGBoost
- Linear Regression
- Random Forest
- AdaBoost

Each model is trained using time series cross-validation.

## Evaluation

Models are evaluated using various metrics:

- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- R-squared (R2) Score

The best-performing model is selected based on these metrics across multiple time series folds.

## Feature Engineering

The project includes several feature engineering steps:

- Creating time-based features (hour, day of week, month, etc.)
- Adding lag features to capture yearly patterns
- Checking for seasonality and stationarity in the time series
