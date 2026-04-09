






# Student Academic Performance and Risk Prediction System

## Executive Summary

This project develops a machine learning pipeline to predict student academic outcomes (Graduate, Dropout, or Enrolled) using the "Predict Students' Dropout and Academic Success" dataset. Four classification algorithms were evaluated: Logistic Regression, Decision Tree, Random Forest, and KNN. The Random Forest classifier achieved the best performance with 76.7 percent accuracy and 75.4 percent weighted F1-score. A Streamlit web application was deployed to provide real-time predictions for educational institutions to identify at-risk students early.

## Problem Statement

Student dropout in higher education causes financial losses for universities, creates an inadequately skilled workforce, and hinders student academic progress. Current identification methods are reactive rather than proactive. This project aims to:

- Predict student academic outcomes early
- Identify factors contributing to dropouts and delayed graduations
- Enable institutional stakeholders to take preventive actions

## Dataset Source

| Property | Value |
|----------|-------|
| Dataset Name | Predict Students Dropout and Academic Success |
| Source | Kaggle |
| Link | https://www.kaggle.com/datasets/thedevastator/higher-education-predictors-of-student-retention |
| Domain | Education |
| File Format | CSV (semicolon delimiter) |
| Total Samples | 4,424 student records |
| Total Features | 36 input features + 1 target variable |

## Methodology

### Data Preprocessing

The following operations were performed:

- Data loading using pandas with semicolon separator
- Missing values check - no missing values found
- Duplicate removal - no duplicates found
- Target variable encoding (Dropout=0, Enrolled=1, Graduate=2)
- Train-test split (80:20 with stratification)
- Feature standardization using StandardScaler

### Models Implemented

| Model | Justification |
|-------|---------------|
| Logistic Regression | Baseline linear model, interpretable, fast |
| Decision Tree | Non-linear, easy to visualize, handles mixed data |
| Random Forest | Ensemble method, reduces overfitting, captures complex interactions |
| K-Nearest Neighbors | Instance-based learning, effective for smaller datasets |

### Evaluation Metrics

- Accuracy
- Precision (weighted)
- Recall (weighted)
- F1-Score (weighted)
- Confusion Matrix

## Results

### Model Performance Comparison

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| Random Forest | 76.72% | 75.44% | 76.72% | 75.39% |
| Logistic Regression | 76.84% | 75.00% | 76.84% | 75.31% |
| Decision Tree | 69.72% | 70.19% | 69.72% | 69.94% |
| K-Nearest Neighbors | 66.78% | 64.83% | 66.78% | 65.53% |

**Best Model:** Random Forest (selected based on highest F1-score)

### Classification Report for Random Forest

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Dropout | 0.81 | 0.75 | 0.78 | 284 |
| Enrolled | 0.57 | 0.37 | 0.45 | 159 |
| Graduate | 0.78 | 0.92 | 0.85 | 442 |
| Macro avg | 0.72 | 0.68 | 0.69 | 885 |
| Weighted avg | 0.75 | 0.77 | 0.75 | 885 |

### Confusion Matrix Analysis

| Actual / Predicted | Dropout | Enrolled | Graduate |
|--------------------|---------|----------|----------|
| Dropout | 213 | 39 | 32 |
| Enrolled | 59 | 59 | 41 |
| Graduate | 18 | 18 | 406 |

**Interpretation:**
- 406 out of 442 Graduates correctly identified (92 percent)
- 213 out of 284 Dropouts correctly identified (75 percent)
- Only 59 out of 159 Enrolled correctly identified (37 percent)

## Demonstration of the Application

### Streamlit Web Application

The final model was implemented using Streamlit which allows users to input student information and get instant predictions.

### Application Features

- Sidebar interface with input forms for all 36 variables
- Real-time prediction using the trained Random Forest model
- Prediction output showing: Dropout, Enrolled, or Graduate
- Probability percentages for each outcome

### Live Deployment

Access the application here: https://github.com/streamlit/streamlit/tree/e490c52b801cdec4f9b2c78e61773494dc1589ae

### How to Use

1. Enter all 36 student information fields in the sidebar
2. Click the "Predict Student Outcome" button
3. View the prediction result and probability percentages

# Conclusion:
In conclusion, this project has been successful in building an end-to-end machine learning pipeline to forecast the performance of students based on a real-world dataset on education. It is notable that the Random Forest algorithm performed best, with an accuracy rate of 77%, while being able to detect which students were likely to dropout. The "Enrolled" class poses difficulties because of the overlapping attributes between "Dropouts" and "Graduates."
The Streamlit app offers a practical solution to educational organizations' retention strategies.


 # Acknowledgment:

We would like to extend our heartfelt appreciation to:

Sir Nazmirul Izzad Bin Nassir for all the support he provided us in this work.
City University Malaysia, Faculty of Information Technology for offering the resources needed for this work.
The providers of the "Predict Students' Dropout and Academic Success" Dataset available on Kaggle.
Open-source communities of Python, Scikit-learn, Pandas, Matplotlib, and Streamlit.

project/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   ├── 1_Dataset_Preprocessing.ipynb
│   ├── 2_Model_Development.ipynb
│   └── 3_Model_Testing.ipynb
│
├── models/
│   ├── best_model.pkl
│   ├── scaler.pkl
│   ├── label_encoder.pkl
│   └── model_comparison_results.csv
│
├── src/
│   └── app.py
│
└── slides/
    └── presentation.pdf
```bash
streamlit 
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
pip install -r requirements.txt
streamlit run src/app.py
