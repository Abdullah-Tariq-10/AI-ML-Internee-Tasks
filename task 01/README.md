# AI/ML Internee Tasks (1-6)

# Task 1: Exploratory Data Analysis (Iris Dataset)

## 📌 Overview
This project focuses on the fundamental steps of data science: loading, inspecting, and visualizing a dataset to understand its underlying structure. Using the classic **Iris dataset**, this script demonstrates how to identify feature distributions, correlations, and potential outliers through statistical summaries and graphical plots.

## 🎯 Objectives
* Load and inspect data using **Pandas**.
* Generate descriptive statistics to understand feature ranges.
* Visualize relationships between features using **Seaborn** and **Matplotlib**.
* Identify the separability of different Iris species based on physical measurements.

## 🛠️ Technologies Used
* **Python 3.x**
* **Pandas:** For data manipulation and statistical summary.
* **Seaborn:** For high-level statistical data visualization.
* **Matplotlib:** For plot customization and layout management.

## 📊 Key Steps & Visualizations

### 1. Data Inspection
The script starts by loading the dataset and printing basic information:
* **Shape:** (150 rows, 5 columns).
* **Features:** `sepal_length`, `sepal_width`, `petal_length`, `petal_width`.
* **Target:** `species` (setosa, versicolor, virginica).

### 2. Statistical Summary
It computes summary statistics (mean, standard deviation, min, max, quartiles) to provide a quick numerical overview of the data distribution.

### 3. Data Visualization
Three specific types of plots were generated to analyze the data:

* **Pairplot (Scatter Matrix):**
    * **Purpose:** To visualize pairwise relationships between all features.
    * **Insight:** Clearly shows that *Iris Setosa* is linearly separable from the other two species based on petal dimensions.

* **Histograms:**
    * **Purpose:** To show the frequency distribution of each feature.
    * **Insight:** Reveals that petal length and width have a bimodal distribution (two distinct peaks), hinting at distinct groups within the data.

* **Box Plots:**
    * **Purpose:** To visualize the spread of data and detect outliers.
    * **Insight:** Highlights the differences in feature ranges across species and identifies specific outliers in the `sepal_width` feature.

## 🚀 How to Run
1.  Ensure you have the required libraries installed:
    ```bash
    pip install pandas seaborn matplotlib
    ```
2.  Run the Jupyter Notebook (`iris_dataset_task_1.ipynb`) or the Python script.