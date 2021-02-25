# Time Series Analysis


## ETS - Error-Trend and Seasonality

Exponentional smoothing
Trend methods models
ETS decomposition All these are related to the general idea of ETS model.
When working with a time series data you will have a

error term
trend term
seasonality term Based of these factors we can fit a model for our data.
How to break down time series into each of these terms?

Time series decomposition is a good way to get those three terms. and visualising those will be a good way to check their behavior.
after plotting the graph will give 4 rows of visualisation which will consist of
observed (actual data)
Trend (the trend line of the data)
Seaonality (if the data is seasonal or not)
residual (the error term which means that it is not explained by the seasonl term or the trend term)

## EWMA - Exponentially Weighted Moving Average

We can improve simple moving average by calculating exponential moving average. Simple moving avg has a weakness
  1. A smaller window will create more noise than signal.
  2. Its always going to lag by the size of the actual window (you will always have missing data at the very first point
  3. Its never going to actually going to reach the full peak or value of the data due to averaging.
  4. It aslo doesnt inform you about future behavior all it does is inform about the trend in the data.
  5. Extreme historical values can skew your sma significantly
In order to fix some of these issues we are going to use EWMA ( exponentially-weighted moving average) How does it work?
  1. It will allow us to remove the lag effect from a sma.
  2. It will put more weight on values that occured more recently ( therefore, as the values get closer to the present time we actualy apply more weight to the        values while calculating the average.
  3. The amount of weight appled will be based on the parameters and teh number of periods given. you can play around with that in pandas untill you get the          desired result.

## ARIMA

ARIMA and ARMA are used to better understand the data or predict the future (forecasting)

### ARIMA has 2 types
1. seasonal ARIMA
2. non-seasonal arima ARIMA models are applied where data shows evidence of non-stationarity. Generally arima models are denoted as arima(p,d,q), where the           parameters p,d,q are non negetive integers.
    (P) (AR) - auto-regressive
        a. it means it utilises the dependent relationship between the current obdervation and the previous ovservations (this is basic regression task)
    (d) integrated
        b. Subtracting an observation from an observation at the previous time step so as to remove stationary.
    (q) (MR) Moving Average
        c. MA used dependency between an observation (1) and a residual error from a moving average model applied to lagged observations (2).
        Stationary vs Non Stationary

### Stationary

A Stationary data set has a constant mean and variance overtime. A stationary data set will allow our models to predict that mean and variance will be same in future periods. Variance should not ba a function of time. Covariance should not be a function of time( which means how fast the variance is changing over time ). You dont have to look at the graphs and test it there are various mathematical tests for this, the most popular is the augmented dickey fuller test. (how to use with python stats models.
Once i have evaluated that the data is not stationary by using the dickey fuller test then i will have to transform it into stationary.

Simple way to do it is via diffrencing.

## AUTOCOREALTION PLOTS

### ACF (better for identifying MA models)

shows the corelation of the time series with itself lagged by x amount of time units.
if autocorrealtion plot shows positive autocorelation at the first lag then it suggests to use the AR terms in relation to thr lag.

if autocorealtion plot shows negative autocorealtion at the first lag then it suggests to use the MA terms in the relation to the lag

P - number of lag observations in the model
D - number of times the raw observations are differenced
Q- size of the moving average window. also called the order of the moving average
PACF (better for identifying AR model)

Conditional Correaltion eg a regression - y = x1,x2,x3. The partial correaltion b/w y & x3 is the correaltion b/w the variables determined taking into account how both y and x3 are related to X1 and X2
A sharp dropoff after lag-K suggests we should use AR-K model
A gradual decline suggests MA model
