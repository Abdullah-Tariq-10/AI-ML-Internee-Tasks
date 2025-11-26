# AI/ML Internee Tasks (1-6)

# Task 3: Heart Disease Prediction (Binary Classification)

## 📌 Overview
This project builds a machine learning classification model to predict whether a patient is at risk of heart disease based on their medical attributes. Using the **UCI Heart Disease dataset**, the script performs extensive data cleaning and feature engineering before training a **Logistic Regression** model to classify patients into "Disease" or "No Disease" groups.

## 🎯 Objectives
* **Clean and Preprocess Data:** Handle missing values and encode categorical variables (like chest pain type and resting ECG).
* **Feature Engineering:** Convert the multi-class target variable (0-4) into a binary target (0 = Healthy, 1 = Disease) for clearer prediction.
* **Train a Classification Model:** Use Logistic Regression to find the relationship between risk factors and heart disease.
* **Evaluate Performance:** Use industry-standard metrics like **ROC-AUC**, **Accuracy**, and the **Confusion Matrix**.
* **Interpret Results:** Identify which medical features (e.g., chest pain, number of vessels) are the strongest predictors of disease.

## 🛠️ Technologies Used
* **Python 3.x**
* **Pandas & NumPy:** For data manipulation and cleaning.
* **Scikit-Learn:** For preprocessing (`StandardScaler`, `OneHotEncoder`), model training (`LogisticRegression`), and evaluation.
* **Matplotlib & Seaborn:** For visualizing the confusion matrix, ROC curve, and feature importance.

## 📊 Methodology

### 1. Data Cleaning & Preparation
* **Missing Data:** Rows with missing values were removed to ensure high data quality.
* **Categorical Encoding:** Text features like `sex`, `cp` (chest pain), and `thal` were converted into numerical format using **One-Hot Encoding**.
* **Target Transformation:** The original dataset labeled disease severity from 0 to 4. This was converted into a binary classification problem:
    * `0` $\rightarrow$ **No Disease**
    * `1, 2, 3, 4` $\rightarrow$ **Disease**

### 2. Model Training
* The data was split into training (80%) and testing (20%) sets.
* **Scaling:** All features were standardized using `StandardScaler` to ensure the Logistic Regression model could weigh coefficients fairly.

## 📈 Key Results

### Model Performance
* **Accuracy:** ~90.00%
* **ROC-AUC Score:** ~0.9417
    * An AUC score close to 1.0 indicates the model is excellent at distinguishing between positive and negative cases.

### Feature Importance
The model identified several critical indicators. The strongest predictors included:
* **`ca` (Number of Major Vessels):** Positive correlation with heart disease.
* **`cp` (Chest Pain Type):** Specific types of chest pain (like non-anginal) were strong indicators.
* **`sex_Male`:** Being male was associated with a higher risk in this dataset.

## 🚀 How to Run
1.  Ensure you have the dataset `heart_disease_uci.csv` in the same directory.
2.  Install dependencies:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```
3.  Run the notebook or script:
    ```bash
    python heartDisease_predict_task_3.ipynb
    ```

