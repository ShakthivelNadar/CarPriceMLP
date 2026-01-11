# Car Price Prediction using Linear Regression

## Overview
This project aims to predict car prices using a Linear Regression model. The goal is to build a robust model that can estimate the price of a car based on various features such as its specifications, make, and other relevant attributes.

## Dataset
The dataset used for this project is `CarPrice_Assignment.csv`. It contains information about various cars and their corresponding prices. Key features include:
- `symboling`: Insurance risk rating
- `wheelbase`: Wheelbase of the car
- `carlength`: Length of the car
- `carwidth`: Width of the car
- `carheight`: Height of the car
- `curbweight`: Curb weight of the car
- `enginesize`: Engine size
- `boreratio`: Boreratio
- `stroke`: Stroke
- `compressionratio`: Compression ratio
- `horsepower`: Horsepower
- `peakrpm`: Peak RPM
- `citympg`: City miles per gallon
- `highwaympg`: Highway miles per gallon
- `CarName`: Make and model of the car
- `fueltype`: Fuel type (gas or diesel)
- `aspiration`: Aspiration type
- `doornumber`: Number of doors
- `carbody`: Body style of the car
- `drivewheel`: Drive wheel type
- `enginelocation`: Engine location
- `enginetype`: Engine type
- `cylindernumber`: Number of cylinders
- `fuelsystem`: Fuel system

The target variable for prediction is `price`.

## Methodology

### 1. Data Loading and Initial Inspection
- The dataset was loaded into a pandas DataFrame.
- The `car_ID` column was dropped as it is not relevant for prediction.

### 2. Feature Engineering / Preprocessing
- **Categorical Feature Encoding**: Categorical features (e.g., `CarName`, `fueltype`, `aspiration`, `doornumber`, `carbody`, `drivewheel`, `enginelocation`, `enginetype`, `cylindernumber`, `fuelsystem`) were converted into numerical format using one-hot encoding with `pd.get_dummies`. The `drop_first=True` argument was used to avoid multicollinearity.

### 3. Data Splitting
- The preprocessed data was split into training and testing sets using `train_test_split` from `sklearn.model_selection`. A `test_size` of 0.2 (20% for testing) and `random_state` of 42 were used for reproducibility.

### 4. Model Training
- A Linear Regression model (`LinearRegression` from `sklearn.linear_model`) was initialized and trained on the training data (`x_train`, `y_train`).

## Model Evaluation

### 1. Model Coefficients
- The intercept and coefficients of the trained Linear Regression model were inspected to understand the impact of each feature on the car price.

### 2. Prediction on Test Data
- The trained model was used to make predictions on the test set (`x_test`).

### 3. Performance Metrics
- The model's performance was evaluated using the R-squared score, which indicates the proportion of variance in the dependent variable that can be predicted from the independent variables.
- An R-squared score of **86.71%** was achieved, indicating that the model explains a significant portion of the variance in car prices.

## Usage

To use this model for prediction on new data, follow these steps:

1.  **Prepare New Data**: Create a pandas DataFrame for the new car(s) you want to predict prices for. Ensure that the new data has the same columns and order as the `x_train` DataFrame after one-hot encoding.
2.  **Make Predictions**: Use the trained `mlr` model's `predict()` method with your prepared new data.

**Example:**
```python
# Create new data with the same structure as the training data
# Here, we copy the first row of x_train and modify some values for demonstration
new_data = x_train.iloc[0:1].copy()
new_data["enginesize"] = 200
new_data["horsepower"] = 150
new_data["curbweight"] = 3000
new_data["citympg"] = 25
new_data["highwaympg"] = 32

# Predict the price for the new data
new_predictions = mlr.predict(new_data)
print("Predictions for new data:", new_predictions)
```

This will output the predicted price for the new car(s).
