# ULD_prediction
A mockup data set and do a Python prediction .

## Step 1 Complete: ULD_Details Parsed
parsed ULD_Details into individual columns:

| FlightID | Aircraft | Origin | Destination | P1P | RKN | AKE | AMJ | PMC |
| -------- | -------- | ------ | ----------- | --- | --- | --- | --- | --- |
| RG559    | B737     | DXB    | SIN         | 12  | 0   | 17  | 0   | 0   |
| RG891    | B787     | LAX    | SYD         | 0   | 9   | 0   | 0   | 0   |
| ...      | ...      | ...    | ...         | ... | ... | ... | ... | ... |


## Step 2: Forecasting Total_ULDs

Clean and convert Total_ULDs into numeric.

Select features: aircraft, origin, destination, ULD types.

Encode categorical variables.

Train a regression model (e.g., RandomForestRegressor).

Evaluate with metrics.


# Data Processing and Model Training Overview

## Import Libraries
- Imports necessary libraries from scikit-learn for:
  - Data splitting
  - Model creation
  - Preprocessing
  - Evaluation
- Imports numpy for numerical operations and specifically imports `LinearRegression`.

## Data Cleaning and Preparation
- Filters out rows where `Total_ULDs` cannot be converted to a number and converts the column to an integer type.
- Converts the `Aircraft`, `Origin`, and `Destination` columns to string type to ensure consistency before encoding.

## Define Features and Target
- Defines the list of features (`features`) for training, including:
  - Categorical columns: `Aircraft`, `Origin`, `Destination`
  - Columns representing counts of different ULD types (from `uld_df` DataFrame).
- Defines the target variable (`y`) as the `Total_ULDs` column.

## Create Preprocessing Pipeline
- Uses `ColumnTransformer` to apply different preprocessing steps to different columns:
  - Applies `OneHotEncoder` to categorical features (`Aircraft`, `Origin`, `Destination`) to convert them into a numerical format.
    - `handle_unknown='ignore'` is used to manage unseen categories during prediction.
  - `remainder='passthrough'` ensures other columns (ULD type counts) are passed through without transformation.

## Create Machine Learning Pipeline
- Creates a `Pipeline` that combines the preprocessing step (`preprocessor`) and the machine learning model (`LinearRegression`).
- Ensures consistent application of preprocessing steps to both training and testing data.

## Split Data
- Splits the data into training and testing sets using `train_test_split`:
  - 80% of the data is used for training (`X_train`, `y_train`).
  - 20% is used for testing (`X_test`, `y_test`).
  - `random_state=42` ensures consistent splits across runs.

## Train the Model
- Trains the `LinearRegression` model using the training data (`X_train`, `y_train`).
- The pipeline automatically applies preprocessing steps before training.

## Make Predictions
- Makes predictions on the test data (`X_test`) using the trained model.

## Evaluate the Model
- Calculates and prints the Root Mean Squared Error (RMSE) to measure the average difference between predicted and actual `Total_ULDs` values.
  - A lower RMSE indicates better accuracy.
- Calculates and prints the R-squared score, representing the proportion of variance in the target variable predictable from the features.
  - An R-squared score close to 1 indicates a good fit.

## Summary
This process takes the cleaned and transformed data, prepares it for a linear regression model, trains the model, and evaluates its performance using RMSE and R-squared.
