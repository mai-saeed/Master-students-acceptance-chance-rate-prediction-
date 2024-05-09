# Master-students-acceptance-chance-rate-prediction-
Explore the data, preprocess the data, and apply machine learning regressors based on their scores, GPA and university rating, among models the random forest regressor has the best MSE score of 0.0025.

## The Structure of the Dataset
This dataset is designed for predicting Graduate Admissions and includes parameters crucial during Master's Program applications. The dataset comprises the following features:

1. GRE Scores (out of 340)
2. TOEFL Scores (out of 120)
3. University Rating (out of 5)
4. Statement of Purpose (out of 5)
5. Letter of Recommendation Strength (out of 5)
6. Undergraduate GPA (out of 10)
7. Research Experience (either 0 or 1)
8. Chance of Admit (ranging from 0 to 1)

All features in the dataset are numerical values. It consists of 900 rows and 8 columns, with 7 independent variables and "Chance of Admit" as the dependent variable.

## Project Approach

1. **Import Libraries:** Begin by importing necessary libraries.
2. **Data Collection:** Gather the data for training and testing.
3. **Exploratory Data Analysis (EDA):**
    - Conduct statistical analysis to understand correlations, means, standard deviations, etc.
    - Visualize each variable (univariate) and each variable with the dependent variable (bivariate).
4. **Data Preparation and Manipulation:**
    - Remove indexing columns.
    - Remove outliers using Interquartile Range (IQR).
      ![image](https://github.com/mai-saeed/Master-students-acceptance-chance-rate-prediction-/assets/77241195/ba7d10b1-7264-4844-9f23-f2d4cb07c673)

    - Check for missing and invalid data.
5. **Data Preprocessing:**
    - Split dependent and independent variables.
    - Split data into training (80%) and testing (20%).
6. **Feature Selection:**
    - **Filtering Methods:**
      			pick up the intrinsic properties of the features measured via univariate statistics instead of cross-validation performance, faster and less computationally expensive than wrapper methods.
        - **Fisher's Score**
          >a.	one of the most widely used supervised feature selection methods.<br>
          >b.	returns the ranks of the variables based on the fisher’s score in descending order.

        - **Correlation Coefficient**
          >a.	Correlation is a measure of the linear relationship of 2 or more variables.<br>
          >b.	Through correlation, we can predict one variable from the other, so if the correlation between an independent variable and the dependent variable is high it will be selected, and if the correlation between two independent variables is high so one of them is enough to select.<br>
          >c.	 Pearson Correlation (f_regression) used in our model and selected by KBest.

        - **Variance Threshold**
    - **Wrapper Methods:**
        - **Recursive Feature Elimination (RFE)**
          >a.	search the space of all possible subsets of features, assessing their quality by learning and evaluating a classifier with that feature subset.<br>
          >b.	the feature selection process is based on a specific machine learning algorithm that we are trying to fit on a given dataset.<br>
          >c.	better predictive accuracy than filter methods.
![image](https://github.com/mai-saeed/Master-students-acceptance-chance-rate-prediction-/assets/77241195/8d3e17d3-48e1-48b1-810e-b2d9395caa46)

    - **Embedded Methods:**
      The main goal of feature selection’s embedded method is learning which features are the best in contributing to the accuracy of the machine learning model. They have built-in penalization functions to reduce overfitting
      >Note: This model doesn’t have overfitting, but it used to apply it and try what if it used over this model, but not predicted it works well.
        - **Lasso**performs L1 regularization, like linear regression, but it uses a technique “shrinkage” where the coefficients of determination are shrunk towards zero to avoid overfitting and make them work better on different datasets. 

        - **Ridge** performs L2 regularization, identical to lasso Regression, the only difference is the absolute value as opposed to the squaring the weights

7. **Dimension Reduction by PCA:** A technique that is used to reduce the dimensions of the dataset. ML models with many input variables or higher dimensionality tend to fail when operating on a higher input dataset. PCA helps in identifying relationships among different variables & then coupling them.
8. **Training and Prediction:**
    - Multiple Linear Regression:
        - The first model with all data variables without Feature selection or PCA
        - model after Fisher’s Score feature selection
        - model after Correlation Coefficient feature selection
        - model after Variance Threshold feature selection
        - model after Recursive Feature Elimination
        - Lasso regression model
        - ridge regression model
        - model after PCA
    - Polynomial Regression
    - Random Forest
9. **Evaluation:**
    - Train and test scores (accuracy)
    - Mean Squared Error (MSE)

Models are sorted by ascending MSE values.

| Model                                                 | Train score | Test score | MSE             |
|-------------------------------------------------------|-------------|------------|-----------------|
| Random forest                                         | 0.9886      | 0.8740     | 0.0025          |
| Multiple linear regression and RFE                    | 0.8146      | 0.7628     | 0.0047          |
| Multiple linear regression                           | 0.8216      | 0.7527     | 0.0049          |
| Ridge regression                                      | 0.8216      | 0.7526     | 0.0049          |
| Multiple linear regression after PCA                  | 0.8019      | 0.7366     | 0.0052          |
| Polynomial regression                                | 0.8568      | 0.7352     | 0.0052          |
| Multiple linear regression and Correlation Coefficient feature selection | 0.8133 | 0.7227     | 0.0055          |
| Multiple linear regression and Variance Threshold feature selection    | 0.7621 | 0.6915     | 0.0061          |
| Multiple linear regression and Fisher Score feature selection           | 0.7182 | 0.6587     | 0.0067          |
| Lasso regression                                      | 0.2142      | 0.1967     | 0.0158          |


