# Fare Prediction Using Machine Learning

## Project Overview

This project implements a machine learning model to predict taxi fare amounts using a minimal and carefully selected set of features. Although the dataset contains multiple ride-related variables, the model is intentionally trained using only two inputs: distance and pickup location.

The primary focus of this project is correct feature selection, avoidance of data leakage, and realistic model behavior rather than achieving inflated accuracy through inappropriate variables.

---

## Problem Statement

The objective is to predict the taxi fare using features that are logically valid for fare estimation. Features that are post-ride, target-derived, or weakly related to fare are excluded to ensure that the model remains interpretable and realistic.

---

## Dataset

The dataset used in this project is the built-in **taxis** dataset from the Seaborn library.  
It contains a variety of numerical and categorical variables related to taxi rides, including distance, pickup and dropoff information, passenger count, payment details, tips, tolls, and total fare components.

While the dataset includes information recorded at different stages of a ride, **only a subset of features is used for model training**, as described below.

---

## Environment and Tools

The project was developed in a Google Colab environment using an NVIDIA T4 GPU.

Libraries used:
- Python
- pandas
- numpy
- seaborn
- matplotlib
- scikit-learn

---

## Exploratory Data Analysis

Exploratory Data Analysis was conducted to understand relationships between features and the target variable.

- Correlation analysis was performed for numerical variables using a heatmap.
- Visual analysis was performed for categorical variables using plots.

Several variables showed high correlation with fare; however, many of these were identified as post-ride or target-derived and were therefore excluded from modeling.

EDA was used strictly as an analysis tool, not as the sole criterion for feature inclusion.

---

## Feature Selection

Although the dataset contains multiple columns, the final model uses **only the following two features**:

- **distance**  
  Selected due to its strong and logical relationship with fare.

- **pickup_zone**  
  Selected to capture geographical variation in fare. This feature was encoded using label encoding.

All other variables present in the dataset were excluded due to one or more of the following reasons:
- They are available only after ride completion (e.g., tip, tolls, total).
- They are directly derived from the target variable.
- They show weak or inconsistent relationships with fare.
- They are not necessary for the scope of this model.

This ensures that the model remains simple, interpretable, and free from data leakage.

---

## Model Development

A **Linear Regression** model was used to predict taxi fares.

The dataset was split into training and testing sets.  
The categorical feature `pickup_zone` was encoded prior to model training.

### Model Configuration
- Model: Linear Regression
- Target Variable: fare
- Features Used: distance, pickup_zone

---

## Evaluation Metrics

Model performance was evaluated using:

- **R² Score**  
  Measures how much variance in the fare is explained by the model.

- **Mean Squared Error (MSE)**  
  Measures the average squared difference between predicted and actual fare values.

---

## Results

The Linear Regression model achieved an R² score of approximately 82 percent on the test data.

This performance reflects a realistic evaluation, as the model relies only on distance and pickup location and does not use post-ride or target-derived variables.

---

## Conclusion

This project demonstrates that even a simple linear regression model can provide meaningful predictions when feature selection is performed carefully. By restricting the model to distance and pickup location, the project prioritizes correctness, interpretability, and realistic assumptions over artificially high accuracy.

The project serves as a clean and reliable example of responsible machine learning practice.
