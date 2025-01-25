# Bike Demand Prediction

## Overview
This project focuses on predicting the demand for bikes based on various factors like temperature, weather conditions, season, and holidays. The dataset contains bike rental information, including features such as temperature, humidity, wind speed, and other categorical variables like the season, weekday, and weather conditions. The goal is to build a linear regression model to predict the bike demand count.

## Steps

### 1. Data Understanding and Preprocessing
The first step involves reading the dataset and performing some initial data exploration and cleaning:

- **Reading the Data**: The dataset is read using pd.read_csv().
- **Renaming Columns**: For better readability, some columns are renamed, such as 'yr' to 'year' and 'mnth' to 'month'.
- **Checking for Missing Values**: Missing values are checked and handled.
- **Dropping Unwanted Columns**: Columns that are redundant or not useful for the model, like 'instant', 'dteday', 'casual', and 'registered', are dropped.
- **Encoding Categorical Variables**: Categorical variables like 'season', 'month', 'weekday', and 'weathersit' are encoded to numerical values.
- **Removing Duplicates**: Any duplicate rows are removed from the dataset.

### 2. Data Exploration and Visualization
To understand the relationships between different variables and the target variable, various visualizations are created:

- **Boxplots**: Boxplots are plotted for categorical columns to check for patterns and outliers.
- **Bar Plots**: Bar plots are used to visualize the relationship between categorical features and the target variable.
- **Pair Plot and Correlation Heatmap**: A pair plot and heatmap are generated to understand correlations between numerical variables.

### 3. Data Preparation for Modeling
After exploring the data, the following preprocessing steps are performed:

- **Dummy Variable Creation**: Dummy variables are created for categorical columns like 'season', 'month', 'weekday', and 'weathersit' using pd.get_dummies().
- **Scaling Features**: The numerical features are scaled using MinMaxScaler to normalize the values and bring them into the same range.

### 4. Splitting Data into Train and Test Sets
The dataset is split into training and testing sets using train_test_split(). The training set is used to train the model, and the test set is used to evaluate its performance.

### 5. Building the Linear Regression Model
A linear regression model is built to predict bike demand:

- **Recursive Feature Elimination (RFE)**: RFE is used to select the most important features and eliminate less relevant ones.
- **Variance Inflation Factor (VIF)**: VIF is calculated to check for multicollinearity and remove highly correlated features.
- **Model Fitting**: The linear regression model is trained on the selected features, and multiple iterations are run to optimize the model by removing features with high p-values and high VIF values.

### 6. Residual Analysis and Model Validation
After building the model, residual analysis is performed to validate the assumptions:

- **Normality of Error Terms**: The error terms are plotted to check if they follow a normal distribution.
- **Multicollinearity Check**: The VIF of the selected features is calculated to ensure that there is no multicollinearity.
- **Linearity**: CCPR plots are used to check for linear relationships between predictors and the target variable.
- **Homoscedasticity**: A scatter plot of residuals is checked to ensure constant variance.
- **Independence of Residuals**: The Durbin-Watson statistic is used to check for autocorrelation in residuals.

### 7. Prediction and Evaluation
After the model is validated, it is used to make predictions:

- **Predictions**: The model makes predictions on the test set using the trained linear regression model.
- **R² Score**: The R² score is calculated for both training and testing datasets to evaluate the model's performance.
- **Adjusted R² Score**: The Adjusted R² score is calculated to adjust for the number of predictors in the model.
- **Graphical Evaluation**: A regression plot is generated to visually compare the actual versus predicted values.

### 8. Final Model Equation
The final equation of the model is:
            cnt = 0.1909 + 0.2341 * year - 0.0963 * holiday + 0.4777 * temp - 0.1481 * windspeed + 
            0.0910 * sep - 0.2850 * Light_snowrain - 0.0787 * Misty - 0.0554 * spring + 
            0.0621 * summer + 0.0945 * winter

### 9. Model Evaluation
**Training Data:**
- R²: 0.833
- Adjusted R²: 0.829

**Test Data:**
- R²: 0.8038
- Adjusted R²: 0.7944

The model performs well on both the training and testing datasets, with an R² score of around 80%.

### Conclusion
The final model demonstrates that the demand for bikes depends on factors such as year, temperature, wind speed, weather conditions, and season. The model can be used to predict bike demand and help in better planning and resource allocation.
