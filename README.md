# 📊 Math Score Predictor

An end-to-end Machine Learning project to predict students' **math scores** based on other features. This project demonstrates the complete ML lifecycle including **data processing, model building, packaging, and deployment on AWS** using **Elastic Beanstalk** and **CI/CD pipelines**.

---

## 🧠 Problem Statement

Accurately predicting students' math scores can help educators identify students in need of academic support. Using a regression-based ML model, this project aims to provide a predictive system trained on exam performance data.

---

## 🚀 Features

- ✅ Clean and modular ML pipeline using object-oriented design
- 📊 EDA and feature engineering
- 🧠 Model training & evaluation (R² Score, RMSE, MAE)
- 💾 Model saving & loading using `joblib`
- 🧪 Automated testing of each pipeline stage
- 🔌 REST API for predictions using **Flask**
- ☁️ Deployed on AWS using **Elastic Beanstalk**
- 🔄 Integrated **CI/CD with AWS CodePipeline**

---

## 🛠️ Tech Stack

- **Dataset source**: https://www.kaggle.com/datasets/spscientist/students-performance-in-exams?datasetId=74977
- **Languages**: Python
- **Libraries**: Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Flask
- **Tools**: Git, GitHub, VS Code
- **Cloud & DevOps**: AWS Elastic Beanstalk, CodePipeline, GitHub Actions

---

## 📁 Project Structure
# End-to-End Student Performance Prediction Pipeline

![Project Banner](https://i.imgur.com/8a25j2B.png)

## Overview

This project implements a complete end-to-end machine learning pipeline to predict student math scores. The pipeline covers every stage of a typical ML project, from data ingestion and exploratory data analysis to model training, evaluation, and finally, deployment on a cloud platform.

The core objective is to predict a student's performance in a math test based on various demographic and socio-economic factors like gender, ethnicity, parental level of education, and test preparation. The project culminates in a robust CI/CD pipeline that automates deployment on **AWS Elastic Beanstalk**.

***

## 🚀 Project Pipeline

The project is structured as a modular pipeline, ensuring scalability and maintainability.

1.  **Data Ingestion**: Data is sourced and loaded into the pipeline.
2.  **Exploratory Data Analysis (EDA)**: The data is analyzed to uncover patterns, check for anomalies, and derive insights.
3.  **Data Transformation**: Data is preprocessed, cleaned, and transformed into a format suitable for model training. This includes handling categorical variables and scaling numerical features.
4.  **Model Training**: Multiple regression models are trained and evaluated to find the best-performing algorithm.
5.  **Deployment**: The final model is deployed as a web application on AWS Elastic Beanstalk, with a CI/CD pipeline set up using AWS CodePipeline for automated builds and deployments.

***

## 📊 Exploratory Data Analysis & Insights

The EDA phase, detailed in the `1 . EDA STUDENT PERFORMANCE .ipynb` notebook, revealed several key insights:

* **Gender Performance**: On average, female students have a better overall score than men, whereas males have scored higher in Maths.
* **Lunch Impact**: Students who have a 'standard' lunch perform significantly better than those with a 'free/reduced' lunch.
* **Test Preparation**: Students who complete a test preparation course achieve higher scores across all three subjects.
* **Parental Education**: There is a clear positive correlation between the parental level of education and student scores. Parents with a master's or bachelor's degree tend to have children who score higher.
* **Race/Ethnicity**: Performance varies across different ethnic groups, with 'Group E' students showing the highest average scores and 'Group A' showing the lowest.

![Score Distribution by Gender and Lunch](https://i.imgur.com/k26p4sC.png)

***

## 🤖 Model Training & Evaluation

The model training process, found in `2 . MODEL TRAINING .ipynb`, aimed to predict the `math_score`.

### Preprocessing Steps:
* **Categorical Features**: `gender`, `race_ethnicity`, `parental_level_of_education`, `lunch`, and `test_preparation_course` were one-hot encoded.
* **Numerical Features**: `reading_score` and `writing_score` were scaled using `StandardScaler`.

### Models Evaluated:
A variety of regression models were tested to determine the best fit for the data:
* Linear Regression
* Lasso & Ridge Regression
* K-Neighbors Regressor
* Decision Tree & Random Forest
* AdaBoost, XGBoost, & CatBoost

### Results:
After evaluation, **Linear Regression** and **Ridge Regression** emerged as the top performers, both achieving an **R² Score of approximately 0.88** on the test set. Due to its simplicity and high performance, Linear Regression was chosen as the final model for deployment.

The model's predictions closely align with the actual values, as shown in the regression plot below:

![Actual vs. Predicted Values](https://i.imgur.com/39a6WlV.png)

***

## 🛠️ Technology Stack

* **Languages**: Python
* **Libraries**: Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib, CatBoost, XGBoost
* **Web Framework**: Flask
* **Cloud & DevOps**: AWS Elastic Beanstalk, AWS S3, AWS CodePipeline, Docker, Git, GitHub

***

## ☁️ AWS Deployment Architecture

This project is deployed using a continuous integration and continuous deployment (CI/CD) pipeline on AWS.

1.  **Source**: The code is hosted on GitHub.
2.  **Build & Deploy**: A push to the main branch triggers **AWS CodePipeline**.
3.  **Deployment Environment**: The pipeline automatically builds a Docker container and deploys the Flask application to **AWS Elastic Beanstalk**.

![AWS Architecture](https://i.imgur.com/4l3gK5S.png)

***

## ⚙️ How to Run the Project Locally

### Prerequisites
* Python 3.8+
* Conda or a virtual environment manager

### Steps
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/](https://github.com/)<your-username>/student-performance-prediction.git
    cd student-performance-prediction
    ```

2.  **Create a virtual environment:**
    ```bash
    conda create -n student_performance python=3.8 -y
    conda activate student_performance
    ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the full training pipeline:**
    ```bash
    python src/pipeline/training_pipeline.py
    ```

5.  **Run the prediction pipeline on new data:**
    * Place your data in the `artifact` folder.
    * Execute the script:
        ```bash
        python src/pipeline/prediction_pipeline.py
        ```
        
6.  **Run the Flask application:**
    ```bash
    python app.py
    ```
    Open your browser and navigate to `http://127.0.0.1:5000`.
