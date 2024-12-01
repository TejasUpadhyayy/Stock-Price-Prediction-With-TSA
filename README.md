
# Finance Time Series Analysis and Forecasting Project

## Overview
This project focuses on forecasting financial time series data, specifically the **VWAP (Volume Weighted Average Price)**, using the ARIMA (AutoRegressive Integrated Moving Average) model. The objective is to build a predictive model that accurately forecasts VWAP values and evaluates its performance using key statistical metrics.

---

## Objective
1. Forecast VWAP using historical time series data.
2. Evaluate model performance using statistical error metrics such as RMSE and MAE.
3. Provide visual insights through plots and graphs for better understanding.

---

## Project Workflow

### 1. **Data Loading and Preprocessing**
- The dataset was imported and prepared for analysis by:
  - Handling missing values (if any).
  - Parsing time-series indices to ensure temporal alignment.
  - Normalizing and scaling the VWAP column for model optimization.

### 2. **Exploratory Data Analysis (EDA)**
- Time series data was visualized to uncover trends, seasonality, and anomalies.
- Stationarity was tested using methods like the Augmented Dickey-Fuller (ADF) test.

#### **Sample Time Series Plot**
![VWAP Time Series](images/vwap_time_series.png)

### 3. **Model Selection**
- ARIMA was chosen due to its effectiveness for univariate time series forecasting.
- Hyperparameters for the ARIMA model were tuned using the `auto_arima` function to minimize AIC and BIC scores.

### 4. **Model Training and Forecasting**
- The ARIMA model was trained on the training data.
- Forecasts were generated for the test data.

#### **ARIMA Forecast Visualization**
![ARIMA Forecast](images/arima_forecast.png)

### 5. **Model Evaluation**
- **Root Mean Square Error (RMSE)** and **Mean Absolute Error (MAE)** were computed to assess model performance.

---

## Results and Key Metrics

### Model Performance
- **Root Mean Square Error (RMSE)**: `222.02`
- **Mean Absolute Error (MAE)**: `160.31`

The model demonstrates good performance in tracking VWAP trends, as evident from the low RMSE and MAE values.

#### **Actual vs Predicted Plot**
![Actual vs Predicted](images/actual_vs_predicted.png)

---

## Python Code Highlights

### Data Visualization
```python
df['VWAP'].plot(figsize=(14, 7), title='VWAP Time Series')
```

### Model Training and Prediction
```python
from pmdarima import auto_arima
model = auto_arima(df['VWAP'], seasonal=False, stepwise=True)
forecast = model.predict(n_periods=len(test_data))
```

### Model Evaluation
```python
from sklearn.metrics import mean_absolute_error, mean_squared_error
rmse = np.sqrt(mean_squared_error(test_data['VWAP'], test_data['Forecast_ARIMA']))
mae = mean_absolute_error(test_data['VWAP'], test_data['Forecast_ARIMA'])
```

---

## Conclusion
The ARIMA model successfully forecasts VWAP values with reasonable accuracy, making it a valuable tool for financial analysis. However, there is potential to enhance the model by:
1. Incorporating exogenous variables such as trading volume or market sentiment.
2. Exploring other machine learning models, e.g., LSTM or Prophet, for better accuracy.
3. Extending the analysis to capture seasonal and cyclical patterns in data.

---

## Future Work
- Integration of external factors (macroeconomic indicators, sentiment analysis).
- Application of advanced deep learning methods for time series forecasting.
- Comprehensive backtesting to validate model robustness under real-world scenarios.

---

## Repository Structure
- `data/`: Contains the dataset used for analysis.
- `notebooks/`: Includes the Jupyter notebook with all code and analysis steps.
- `images/`: Contains visualizations and plots generated during the project.

---

## How to Use
1. Clone the repository:
   ```
   git clone https://github.com/your-username/finance-time-series-forecasting.git
   ```
2. Navigate to the project directory:
   ```
   cd finance-time-series-forecasting
   ```
3. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
4. Run the Jupyter notebook:
   ```
   jupyter notebook notebooks/finance_time_series_analysis.ipynb
   ```

---

## Dependencies
- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- statsmodels
- pmdarima
- scikit-learn

---

## Acknowledgments
This project is inspired by real-world financial forecasting challenges. Special thanks to the open-source contributors who maintain the tools and libraries used in this analysis.

---

## Author
**Your Name**  
[Your GitHub Profile](https://github.com/TejasUpadhyayy)
