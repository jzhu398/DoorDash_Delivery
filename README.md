# DoorDash_delivery

Order lateness/underprediction of delivery time is of particular concern as past experiments suggest that underestimating delivery time is roughly twice as costly as overestimating it. Thus, It is very important for food delivery companies to get this right. In this project, I will build a model to estimate delivery time.

## Data Processing


For this project, A historical data is provided with 197428 records. I formed target using actual_delivery_time, created_at, estimated_store_to_consumer_driving_duration, and estimated_order_place_duration. I also tried to form target using actual_delivery_time and created_at. Several columns from the dataset contain some missing values. I fill up missing with its median/medium values for each column. Creating different ratio features or duration features to help model predict. Moreover, Some columns contain negative values, which didn’t make sense. I simply make those negative numbers to 0. There are outliers in actual delivery time. Therefore, I remove those outliers as well. One-hot-encoded categoricial features to boolen features.


## EDA
First, I looked up the numerical features' distribution.
Second, I removed redundant and collinear features by using corr.
Then, I removed features that could cause multicollinearity by using VIF.
After that, a quick fowward/backward feature selections by model and pairplot. In this project, PCA could help merge many features as one-hot enoding creates too many features to feed model.
Finally, scale all training set to make every feature uniform weight at the beginning.


## Models and Results

In this section, I’ve tried several different Machine Learning models such as Ridge regression, XGBRegression, and LGBRegression. I’ll evaluate the performance by RMSE and pick the best one.

|      |RMSE    |
|------------|-------------|
| Ridge Regression Out-sample|2055.36|
| Ridge Regression In-sample|1074.5|
| XGBRegression Out-sample|2039.21|
| XGBRegression In-sample|976.43|
| LGBRegression Out-sample|1047.63|
| LGBRegression In-sample|598.82|

The best model is the LGBRegression

# Note
** raw data: historical_data.csv

** python file: doordash.ipynb (data process, analysis, model), data_process.py (helper function)


