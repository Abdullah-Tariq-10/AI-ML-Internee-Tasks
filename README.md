# AI/ML Internee Tasks (1-6)

# 🤖 AI/ML Engineering Internship - DevelopersHub Corporation

## 📌 Internship Overview
This repository contains the complete portfolio of tasks submitted for the **AI/ML Engineering Internship at DevelopersHub Corporation**.

The goal of this internship is to build a strong foundation in artificial intelligence and machine learning by tackling real-world problems. The projects range from fundamental data exploration and classical regression/classification to advanced large language model (LLM) fine-tuning and prompt engineering.

**Status:** ✅ All 6 Tasks Completed  
**Due Date:** 28th November 2025

---

## 🚀 Project Dashboard

| Task | Objective | Model / Approach | Key Result / Finding |
| :--- | :--- | :--- | :--- |
| **1. Iris EDA** | Visualize dataset trends & distributions | Pandas, Seaborn, Matplotlib | Confirmed *Iris Setosa* is linearly separable based on petal dimensions. |
| **2. Stock Prediction** | Predict next-day closing price (AAPL) | Linear Regression (Time Series) | **R² $\approx$ 0.96**. High accuracy due to market continuity (predicting near previous close). |
| **3. Heart Disease** | Predict heart disease risk (Binary) | Logistic Regression | **ROC-AUC $\approx$ 0.94**. Key risk factors identified: `cp` (chest pain) and `ca` (vessels). |
| **4. Health Chatbot** | Answer general health queries safely | Mistral-7B (Hugging Face API) | Implemented strict **Prompt Engineering** guardrails and mandatory medical disclaimers. |
| **5. Empathetic Bot** | Fine-tune LLM for mental health support | **Qwen 1.5B (QLoRA, PEFT)** | Fine-tuned an instruction model to prioritize validation over advice; implemented hard safety guardrails. |
| **6. House Prices** | Predict property prices | Linear Regression vs. Gradient Boosting | **Linear Regression** outperformed GB (MAE: $\approx$ \$243k), indicating the dataset patterns were predominantly linear. |

---

## 📂 Task Summaries

### 🔹 Task 1: Exploring and Visualizing a Simple Dataset
* **Objective:** Load, inspect, and visualize the Iris dataset to understand data distributions.
* **Tech Stack:** Pandas, Seaborn, Matplotlib.
* **Key Work:**
    * Generated **Pairplots** to visualize feature correlations.
    * Used **Box Plots** to identify outliers in `sepal_width`.
    * Confirmed distinct clustering of species.

### 🔹 Task 2: Predict Future Stock Prices (Short-Term)
* **Objective:** Use historical data to predict the next day's closing price for Apple (AAPL).
* **Tech Stack:** `yfinance`, Scikit-Learn (Linear Regression).
* **Key Work:**
    * Fetched data from Yahoo Finance (2020-2023).
    * Engineered a supervised learning target by shifting `Close` prices by -1 day.
    * **Insight:** While metrics were high (MSE ~4.96), the model primarily learned to follow the trend rather than predict market shocks.

### 🔹 Task 3: Heart Disease Prediction
* **Objective:** Build a binary classification model to assess heart disease risk.
* **Tech Stack:** Logistic Regression, StandardScaler, OneHotEncoder.
* **Key Work:**
    * Transformed multi-class targets (0-4) into binary (0 vs 1+).
    * Achieved **90% Accuracy**.
    * **Visuals:** Confusion Matrix and ROC Curve showing excellent class separation.

### 🔹 Task 4: General Health Query Chatbot
* **Objective:** Create a safe, helpful AI assistant for general health questions.
* **Tech Stack:** Hugging Face Inference API (`mistralai/Mistral-7B-Instruct-v0.2`).
* **Key Work:**
    * **Prompt Engineering:** Designed a system prompt with a specific persona ("HealthBot").
    * **Safety:** Hard-coded instructions to refuse diagnosis/prescriptions and handle emergency queries by referring to emergency services (1122).

### 🔹 Task 5: Mental Health Support Chatbot (Fine-Tuned)
* **Objective:** Fine-tune a Large Language Model (LLM) to provide supportive, empathetic, and safe responses for emotional wellness.
* **Tech Stack:** `Qwen-1.5B-Instruct`, **QLoRA** (Peft, BitsAndBytes), Hugging Face `trl`.
* **Key Work:**
    * **Efficient Fine-Tuning:** Used **4-bit quantization** and Low-Rank Adaptation (LoRA) to fine-tune a 1.5B parameter model on a free GPU.
    * **Data Processing:** Cleaned the `EmpatheticDialogues` dataset to remove formatting artifacts and filter out low-quality responses.
    * **Safety Engineering:** Implemented hard-coded **guardrails** to intercept crisis keywords (e.g., self-harm) and redirect users to professional help *before* the model generates a response.

### 🔹 Task 6: House Price Prediction
* **Objective:** Predict housing prices based on features like location and square footage.
* **Tech Stack:** Linear Regression, Gradient Boosting Regressor.
* **Key Work:**
    * **Preprocessing:** Applied Ordinal Encoding to `Condition` and One-Hot Encoding to `Location`.
    * **Comparison:** Evaluated both models. **Linear Regression** provided the lowest error (RMSE ~$280k), indicating that the dataset (randomly generated) lacked the non-linear complexity needed for Gradient Boosting to shine.

---

## 🛠️ Installation & Usage

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/Abdullah-Tariq-10/AI-ML-Internee-Tasks
    cd AI-ML-Internee-Tasks
    ```

2.  **Install dependencies:**
    Each task folder contains specific requirements, but the core libraries used are:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn transformers datasets torch yfinance huggingface_hub accelerate
    ```

3.  **Run a Task:**
    Navigate to any task folder and run the Jupyter Notebook:
    ```bash
    jupyter notebook Task_1_Iris_EDA/Task_1_Iris_EDA.ipynb
    ```

---

**Author:** Abdullah Tariq
**Internship:** DevelopersHub Corporation
