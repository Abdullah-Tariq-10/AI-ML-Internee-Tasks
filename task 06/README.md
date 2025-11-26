# AI/ML Internee Tasks (1-6)

# Task 6: House Price Prediction (Regression)

## 📌 Overview
This project explores regression techniques to predict house prices based on property attributes like square footage, location, and condition. Using a **House Price Prediction Dataset**, the script demonstrates the end-to-end machine learning pipeline: from data cleaning and advanced feature preprocessing to model training and evaluation.

## 🎯 Objectives
* **Data Preprocessing:** Handle mixed data types by applying scaling to numerical features and encoding to categorical ones.
* **Feature Engineering:** transform raw features (e.g., "Excellent", "Downtown") into a machine-readable format using Ordinal and One-Hot encoding.
* **Model Training:** Train a **Linear Regression** model to establish a baseline for price prediction.
* **Evaluation:** Measure model performance using **Mean Absolute Error (MAE)** and **Root Mean Squared Error (RMSE)**.
* **Visualization:** Plot predicted prices against actual prices to visually assess model accuracy.

## 🛠️ Technologies Used
* **Python 3.x**
* **Pandas & NumPy:** For data manipulation and numerical operations.
* **Scikit-Learn:** For preprocessing (`ColumnTransformer`, `StandardScaler`, `OneHotEncoder`), model training (`LinearRegression`), and evaluation.
* **Matplotlib & Seaborn:** For data visualization.

## 📊 Methodology

### 1. Data Preprocessing
A robust preprocessing pipeline was built using Scikit-Learn's `ColumnTransformer`:
* **Numerical Features:** (`Area`, `Bedrooms`, etc.) were scaled using **StandardScaler** to normalize distributions.
* **Ordinal Features:** The `Condition` column was encoded using **OrdinalEncoder**, preserving the logical order: *Poor < Fair < Good < Excellent*.
* **Nominal Features:** The `Location` column was transformed using **OneHotEncoder** (with `drop='first'` to prevent multicollinearity).
* **Binary Encoding:** The `Garage` feature was manually mapped to 0 (No) and 1 (Yes).

### 2. Model Training
We trained a **Linear Regression** model. While more complex models (like Gradient Boosting) were tested, Linear Regression provided comparable results for this specific dataset, suggesting the underlying data patterns are predominantly linear or random.

## 📈 Key Results

### Evaluation Metrics
* **Mean Absolute Error (MAE):** ~$243,453
* **Root Mean Squared Error (RMSE):** ~$280,058

### Insight
The relatively high error rates suggest that the dataset (which is synthetic/randomly generated) lacks the complex, non-linear patterns found in real-world real estate markets. However, the project successfully demonstrates the correct implementation of a regression pipeline for mixed-type data.

## 🚀 How to Run
1.  Ensure `House Price Prediction Dataset.csv` is in the same directory.
2.  Install dependencies:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```
3.  Run the notebook or script:
    ```bash
    python housePrices_predict_task_6.ipynb
    ```