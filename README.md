# Cash demand forecasting of ATMs

#### • Do ⭐ the repository if it helped you in anyway.

## Scope of problem:

ATMs filled with large amounts of cash may bring low transport/logistic cost but high freezing & high insurance cost. 
On the other hand, if banks do not have the proper mechanism to track the usage pattern, then frequent re-filling ATMs will reduce 
freezing and insurance cost but increase logistic cost.
Also, analysing and forecasting the cash demand will help the government to study the cash flow in the economy.


## Data Collection:

I got real world ‘ATM withdrawal value across banks’ data which is published on RBI website.

Source: https://www.rbi.org.in/Scripts/BS_PressReleaseDisplay.aspx?prid=49901


## Data Analysis:

By decomposing the data I got to know that there is dual seasonality weekly as well as monthly. 
However, there is a constant trend present over time. Further, by applying Dickey’s fuller test I got to know that the data is already stationary.

![image](https://user-images.githubusercontent.com/65092456/100250389-a0bde780-2f63-11eb-88a8-beebe0c74133.png)


![image](https://user-images.githubusercontent.com/65092456/100250468-b59a7b00-2f63-11eb-8d30-5b1395ae1b52.png)


## Models used:

I have built our first model using Moving Average method.
For model 2, as the data is stationary, we can apply autoregressive model. 
But the data has seasonality present in it, so I have used Seasonal ARIMA model.

![image](https://user-images.githubusercontent.com/65092456/100250767-0a3df600-2f64-11eb-99bb-e21d3d3b5165.png)

For model 3, we have used auto ARIMA to get the optimized value of the parameters p,d,q.


## Comparative Analysis:

Model 1 is made using Moving Average.
I have built other two models using SARIMAX.
In the second model, I have manually selected the value of parameters p and q based on ACF and PACF plot. 
And as the data is already stationary there was no need to apply differencing and so the value of parameter d is 0.
I have built second model using auto arima to get the optimized value of p and q. The value of d is same as model 2 that is ‘0’.
 
Model 1 RMSE : 330.95 
Model 2 RMSE : 461.65
Model 3 RMSE : 331.14

If we compare the metrics for each model, we see that the RMSE for moving average and auto ARIMA model is approximately same.
However, SARIMAX model considers both AR and MA properties.
Therefore, we can conclude that model 3 is performing better compared to model 1 and model 2.


## Limitations:

We do not have sufficient data to make accurate forecast, however, we can make a forecast for a short period say a week. 
Furthermore, the model can be improved if we have data available for sufficient period.


## Future work:

We can extend this model to forecast the cash demand for individual banks. 
Here, we have the data for ATM withdrawal across bank and so we can forecast the demand in total. 
However, if an individual bank forecasts the demand for their own ATMs, it can benefit them in following ways:

•	Optimizing the logistic and insurance cost,

•	Stabilizing the cash freeze,

•	Improving the customer goodwill and so on.

