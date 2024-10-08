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
├── Dockerfile
├── requirements.txt
├── README.md
```

- `data/`: Contains the dataset used for analysis.
- `notebooks/`: Jupyter notebook with all code.
- `Dockerfile`: Instructions for building the Docker container.
- `requirements.txt`: List of Python dependencies.

## Setup

### Prerequisites

- Docker and Git installed

### Installation

1. Clone this repository:
   ```
   git clone https://github.com/andresruizc/ARC-TestDataScience-2.git
   cd ARC-TestDataScience-2
   ```

2. Build the Docker image:
   ```
   docker build -t jupyter-air-quality  -f Dockerfile .
   ```

3. Run the Docker container:
   ```
   docker run -p 8888:8888 jupyter-air-quality
   ```

4. Open the Jupyter Lab URL provided in the console output in your web browser.
   ```
   http://127.0.0.1:8888/?token=xxxxxxxxxxxxx
   ```
## Usage

### Jupyter Notebook

Once you have the Jupyter interface open in your browser:

1. Open `main.ipynb`.
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

  Here's the reference of the dataset to download the link: https://archive.ics.uci.edu/dataset/381/beijing+pm2+5+data

## Models

The project evaluates several machine learning models:

- XGBoost
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
