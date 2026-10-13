# Severe Vaccine Adverse Event Prediction

A machine learning project focused on predicting severe post-vaccination adverse events and identifying potential risk factors using data from the Vaccine Adverse Event Reporting System (VAERS).

## Overview

Vaccines play an important role in public health, but monitoring adverse events following vaccination is essential for ongoing vaccine safety surveillance. This project explores how machine learning techniques can be applied to vaccination adverse event reports to identify patterns associated with severe outcomes.

Using data from the **Vaccine Adverse Event Reporting System (VAERS)**, maintained by the U.S. Food and Drug Administration (FDA) and the Centers for Disease Control and Prevention (CDC), the project focuses initially on adverse event reports associated with the Pfizer-BioNTech and Moderna mRNA COVID-19 vaccines.

The goal is to develop predictive models that distinguish reports associated with severe outcomes from other reports and investigate which demographic and symptom-related features are most influential in model predictions.

## Objectives

- **Predict severe outcomes:** Develop machine learning models to classify adverse event reports according to severity.
- **Identify potential risk factors:** Examine demographic characteristics and reported symptoms associated with model predictions.
- **Handle imbalanced data:** Explore resampling techniques to address differences in the number of severe and non-severe reports.
- **Compare model performance:** Evaluate multiple classification algorithms using a range of performance metrics.
- **Improve interpretability:** Investigate important features contributing to model predictions.

## Dataset

**Source:** [Vaccine Adverse Event Reporting System (VAERS)](https://vaers.hhs.gov/data.html)

The project uses VAERS data files containing information such as:

- **Demographics:** Age, sex, and other available demographic characteristics.
- **Vaccination information:** Vaccine type and related vaccination details.
- **Reported symptoms:** Symptoms and other information recorded in adverse event reports.
- **Outcome information:** Available indicators used to define the severity of reported events.

The demographic, symptom, and vaccine datasets are combined using the unique `VAERS_ID` identifier.

> **Important:** VAERS is a passive reporting system. Reports describe events occurring after vaccination and do not, by themselves, establish that vaccination caused those events. Model predictions indicate patterns in reported data, not confirmed medical causation or individual clinical risk.

## Methodology

### 1. Data Preprocessing

- Merge demographic, symptom, and vaccine datasets using `VAERS_ID`.
- Remove duplicate records and address invalid or inconsistent data.
- Handle missing values and prepare relevant features.
- Apply one-hot encoding to categorical variables.
- Normalize continuous variables where appropriate.
- Define the target variable representing severe versus non-severe reported outcomes.

### 2. Handling Class Imbalance

Severe adverse event reports may be less common than non-severe reports. The project explores oversampling and undersampling techniques to address class imbalance and improve the models' ability to identify severe cases.

Resampling should be applied to the training data only to avoid information leakage into validation and test sets.

### 3. Dataset Splitting

The planned experimental setup uses a stratified split:

| Dataset | Proportion |
|---|---:|
| Training set | 70% |
| Validation set | 10% |
| Test set | 20% |

Stratification helps preserve the distribution of the target classes across the splits.

### 4. Model Development

The project explores the following classification algorithms:

| Model | Purpose |
|---|---|
| Logistic Regression | Establish a baseline and examine feature relationships |
| Random Forest | Capture nonlinear patterns and feature interactions |
| XGBoost | Explore gradient-boosted decision trees for classification |
| Multilayer Perceptron (MLP) | Investigate nonlinear patterns using a neural network |

Models can be compared using consistent data splits and evaluation procedures.

### 5. Model Evaluation

Performance is assessed using multiple metrics:

- **Accuracy:** Overall proportion of correctly classified reports.
- **Precision:** Proportion of predicted severe cases that are classified as severe.
- **Recall:** Proportion of severe cases correctly identified by the model.
- **F1-score:** Balance between precision and recall.
- **ROC-AUC:** Ability to distinguish between the two classes across classification thresholds.
- **Confusion matrix:** Breakdown of true positives, true negatives, false positives, and false negatives.

Because missing severe cases is an important concern, recall and precision should be considered alongside accuracy rather than relying on accuracy alone.

### 6. Model Interpretability

To investigate which features influence predictions, the project considers:

- Logistic regression coefficients.
- Random Forest and XGBoost feature importance.
- SHAP (SHapley Additive exPlanations) for interpreting feature contributions, where applicable.

These methods can help explain model behaviour but do not establish that a feature causes a severe adverse event.

## Technology Stack

The project is designed around the following tools and techniques:

- **Language:** Python
- **Data processing:** pandas, NumPy
- **Machine learning:** scikit-learn
- **Gradient boosting:** XGBoost
- **Data visualization:** Matplotlib, Seaborn
- **Model interpretability:** SHAP
- **Data source:** VAERS

*The libraries listed above represent the intended technology stack; update this section to reflect the packages actually used in the implementation.*

## Project Workflow

1. Collect and inspect VAERS datasets.
2. Merge demographic, symptom, and vaccine information.
3. Clean the data and engineer relevant features.
4. Define the severity classification target.
5. Split the data into training, validation, and test sets.
6. Apply resampling techniques to the training set where appropriate.
7. Train and tune classification models.
8. Evaluate and compare model performance.
9. Interpret model predictions and investigate influential features.

## Limitations

- VAERS reports may be incomplete, inconsistent, or subject to reporting bias.
- The dataset does not establish a causal relationship between vaccination and reported events.
- Class imbalance may affect model performance, especially for severe outcomes.
- Results may not generalize to other vaccines, populations, or reporting periods.
- Feature importance reflects predictive associations and should not be interpreted as proof of medical risk factors.

This project is intended for educational and research purposes in machine learning and public health data analysis. It is not a clinical diagnostic tool and should not be used to make individual vaccination or treatment decisions.

## Future Improvements

- Evaluate models on additional vaccine types and reporting periods.
- Investigate alternative class-imbalance strategies and decision thresholds.
- Perform more systematic hyperparameter tuning.
- Validate model performance on independent datasets where suitable data are available.
- Improve interpretability and assess the stability of identified features.
- Assess potential demographic disparities and model bias.

## Disclaimer

This project is an independent data science and machine learning study. It does not represent the views of the FDA, CDC, or any other public health organization. VAERS data are subject to limitations, and predictions should not be interpreted as evidence of vaccine causation.

## License

A license has not yet been specified. Add an appropriate license before distributing or reusing the project's code.
