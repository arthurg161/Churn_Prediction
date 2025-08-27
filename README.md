# Customer Churn Prediction with Machine Learning

## Overview
This project aims to predict customer churn — the likelihood of a client leaving a company. By analyzing historical customer data, we can identify risk patterns and create actionable insights to reduce churn.

The process includes:
* Understanding the dataset and cleaning missing values.
* Selecting the most relevant customer features.
* Creating a baseline model for benchmark.
* Building a predictive model to classify customers as likely to churn or likely to stay.
* Validating the model with different datasets (train, test, and out-of-sample) to ensure reliability.
* Visualizing results with ROC curves and a confusion matrix to measure performance.


This type of model can help businesses improve customer retention strategies, reduce losses, and prioritize high-risk clients.


## Business Impact
* Customer Retention: Early identification of high-risk customers enables targeted retention strategies, reducing churn rates.
* Revenue Protection: Lower attrition safeguards recurring revenue streams and maximizes customer lifetime value.
* Strategic Advantage: Data-driven insights strengthen decision-making, improving competitiveness and long-term growth.

---

## Technical Description
The pipeline is implemented in Python using pandas, scikit-learn, and feature-engine libraries.

**1. Data Loading & Exploration:**
   * Load the dataset - availabe [HERE](https://www.kaggle.com/datasets/teocalvo/analytical-base-table-churn/data)
   * Checked missing values and visualized churn distribution.


**2. Feature Engineering & Selection:**
   * Excluded nominal identifiers from features.
   * Split data into in-sample (train/test) and out-of-sample (OOS) for realistic evaluation.
   * Used a Decision Tree to calculate feature importances, keeping variables explaining ~90% of variance.


**3. Benchmark Model – Majority Learner:**
   * Implemented a simple baseline model that always predicts the majority class.
   * Provides a reference point to ensure that the logistic regression and future models outperform a trivial predictor.
     
**4. Pipeline Design:**
   * **Discretization:** Continuous variables transformed into bins (DecisionTreeDiscretiser) based on their relationship with churn. Captures nonlinear effects and reduces sensitivity to outliers, improving model robustness and interpretability.
   * **One-Hot Encoding:** Converted categorical variables (including discretized bins) into binary dummy variables. It allows the model to handle categorical data effectively without imposing a false numerical order.
   * **Logistic Regression:** A linear model widely used in churn prediction due to its interpretability, efficiency, and robustness in binary classification tasks. It allows clear analysis of feature importance via coefficients, making it easier to understand which variables most influence churn. Additionally, it provides probability estimates, supporting business decisions by ranking customers by churn risk. Logistic Regression serves as a strong, transparent baseline before testing more complex models.

**5. Model Evaluation:**
  * Metrics: Accuracy and ROC AUC Score across train, test, and OOS datasets.
  * Visualization: ROC Curves comparing performance across datasets.
  * Confusion Matrix on test set for classification insight.


**6. Results:**
  * The baseline Majority Learner, with 53.12% accuracy and no predictive power (AUC 0.50), highlighted the challenge of churn prediction.
  * Logistic Regression, however, achieved over 72% accuracy on test data and an AUC above 0.80 across all datasets, demonstrating reliable generalization and strong predictive power. This translates into actionable insights for identifying at-risk customers, enabling targeted retention strategies and ultimately protecting revenue streams.


