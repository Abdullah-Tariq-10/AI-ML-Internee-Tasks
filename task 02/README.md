# AI/ML Internee Tasks (1-6)

# Task 2: Short-Term Stock Price Prediction

## 📌 Overview
This project demonstrates how to build a simple time-series forecasting model to predict future stock prices. Using historical data for **Apple (AAPL)**, we train a **Linear Regression** model to predict the *next day's* closing price based on the current day's market features.

## 🎯 Objectives
* Fetch historical financial data using the `yfinance` API.
* Perform feature engineering to create a supervised learning target (Next Day's Close).
* Train a Linear Regression model on time-series data.
* Visualize the difference between actual and predicted stock prices.

## 🛠️ Technologies Used
* **Python 3.x**
* **yfinance:** For retrieving stock market data.
* **Pandas & NumPy:** For data manipulation and shifting.
* **Scikit-Learn:** For model training (`LinearRegression`) and evaluation metrics (`MSE`, `R²`).
* **Matplotlib:** For plotting the prediction results.

## 📊 Methodology

### 1. Data Fetching
We downloaded historical data for **Apple (AAPL)** from **Jan 1, 2020, to Dec 31, 2023**.

### 2. Feature Engineering
* **Features (X):** `Open`, `High`, `Low`, `Volume` (Today's data).
* **Target (y):** We created a new column by shifting the `Close` price **backwards by one day**. This aligns "Today's Data" with "Tomorrow's Price," turning the forecasting problem into a supervised regression problem.

### 3. Model Training
* The data was split into training (80%) and testing (20%) sets.
* **Crucial Step:** We set `shuffle=False` during the split to respect the chronological order of the time-series data.

## 📈 Results & Findings

### Evaluation Metrics
* **Mean Squared Error (MSE):** ~4.96
* **R-squared (R²) Score:** ~0.96

### Key Insight
The model achieved an incredibly high R² score, but this comes with a caveat.
* **The "Continuity" Factor:** In stock markets, the best predictor for tomorrow's price is often simply *today's price*.
* **What the model learned:** The regression model essentially learned that the predicted price is very close to the current `High` or `Low`. While accurate for short-term trends, this simple model cannot predict market *shocks* or sudden direction changes.

## 🚀 How to Run
1.  Ensure you have the required libraries installed:
    ```bash
    pip install yfinance pandas numpy scikit-learn matplotlib
    ```
2.  Run the Jupyter Notebook (`stockPrices_predict_task_2.ipynb`) or the Python script.