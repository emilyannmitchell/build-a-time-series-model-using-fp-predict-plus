# How to build time series model using FP Predict Plus operator hosted on Red Hat Marketplace

Time series analysis comprises methods for analyzing time series data in order to extract meaningful statistics and other characteristics of the data. Time series allows you to analyze major patterns such as trends, seasonality, cyclicity, and irregularity. Time series forecasting is the use of a model to predict future values based on previously observed values. Time series are widely used for non-stationary data, like economic, weather, stock price, and retail sales.

This tutorial demonstrates how to quickly build a time-series model using FP Predict Plus operator with a dataset that shows the how the prices differ over a period of time at a paricular retail store outlet.

## Learning objectives

* Users will learn how to operate with Red Hat Marketplace FP Predict Plus Operator
* Setup a Time-Series Model on FP Predict Plus 
* Learn how to configure the Training and Forecast parameters
* View and analyze the time-series results

## Prerequisites

Please refer to this [link](https://developer.ibm.com/tutorials/get-started-findability-platform-predict-plus-red-hat-marketplace/) for getting started with installation and setup of FP Predict plus operator.

## Estimated time

Completing this tutorial should take about 40 minutes.

## Steps to build the time series model

### Create a new Time-Series Job

* Login to your FP Predict Plus Operator by launching it.

![](doc/src/images/login.png)

* Click on `+ Start` button

![](doc/src/images/start_button.png)

* A prompt will pop-up asking if your data contains Time-Stamp. Select `Yes`.

![](doc/src/images/create_job.png)

* Another prompt will pop-up asking if you will be predicting values. Select `Yes`.

![](doc/src/images/predict_prompt.png)

### Configure the Time-Series Model

* Download the dataset [train.csv](https://github.com/IBM/build-a-time-series-model-using-fp-predict-plus/blob/main/datasets/train.csv)

* Download the dataset [test.csv](https://github.com/IBM/build-a-time-series-model-using-fp-predict-plus/blob/main/datasets/test.csv)

* Enter the details as follows-

  * Enter `Job Name` as `TS` (Pls avoid special characters in the name)
  * Dataset location must be `local`
  * Daily Interval set as `Daily`
  * Tasks `Model + Forecast`
  * Upload training file from the downloaded file `train.csv`
  * Set Target Variable as `item_price`
  
  ![](doc/src/images/training_config.png)

  * Upload the forecast file from the downloaded file `test.csv`
  * Set Timestamp variable as `date`
  * Set Timestamp Format as `dd/mm/yyyy`
  * Click on `Run`
  
  ![](doc/src/images/forecast_config.png)
  
*** Note: It will take about 10 minutes to setup the model, pls wait and don't refresh the page until it's over ****  

### Analyze your Output

After the completion you will receive an output as given below-

  ![](doc/src/images/output.png)

The above graph shows the time-series of prices over the time period 2013 to 2015.

Click on the `analytics` icon to analyze your results

  ![](doc/src/images/analytics_icon.png)
  
  #### Analysis Description
  
  1. The first table on the top left corner, depcits the actual v/s predicted and the difference in prediction for each time        interval. Note that it provides only the head values of the result table
  2. The graph on the top right represents the same output as received on the dashboard
  3. The `Modeling Metrics` and `Forecast Metrics` provides measures of the trained model using techniques such as Mean            Error, Root Mean Square,Mean Percentage Error, Mean Absolute Percentage Error and Mean Absolute Scaled Error. These will      allow us to evaluate how well the underlying model is trained and forecasts.
  4. Log table provides metadata of the trained file, such as the number of rows and time taken to train.
  5. The last table is about the `Important Rows` since ours is a time-series model with only one underlying feature       
     distribution.

  ![](doc/src/images/analyze_results.png)

  ![](doc/src/images/analyze_results_2.png)
  
## Important pointers on the datasets 

* Must have only 2 other columns apart from the date variable which are Row sequence number and Target Variable.
* Ensure the time interval is correctly maintained through the training and forecast data. Eg: If you put the time interval as Daily, your dataset MUST contain only one record for a particular day.
* Additionally, if you set Daily as interval, your forecast data MUST have a forecast for everyday without a gap.

* If you encounter the below error-
  
  ![](doc/src/images/Error.png)
  
  Clear your browser cache or try in another browser.

For further reference, look at the datasets used in this tutorial.
  

## Summary

In summary, this tutorial helps you to understand how to perform time-series analysis using the FP Predict Plus Operator hosted on Red Hat Market Place.

## Related links

* [Predict fraud using FP Predict Plus](https://developer.ibm.com/patterns/predict-fraudulent-transactions-findability-platform-predict-plus/)
* [Predict sales using FP Predict Plus](https://developer.ibm.com/patterns/use-redhat-marketplace-operator-fp-predict-plus-to-predict-sales/)

