## About

This project analyzes 60-month consumer auto loan rates using quarterly data 
from the Federal Reserve Economic Data (FRED) to evaluate which time series 
approach best forecasts rate changes for corporate finance and retail planning 
purposes.

The analysis begins with exploratory diagnostics confirming the data is 
non-stationary, driven by prolonged macroeconomic cycles rather than seasonal 
retail trends. This was confirmed statistically through Augmented Dickey-Fuller 
and KPSS unit root tests, followed by first-order differencing to stabilize the 
series and a Woodward-Bottone-Gray bootstrap test that found no evidence of a 
deterministic trend.

Three forecasting approaches were built and compared:

- **ARIMA(2,1,0)** — a traditional statistical model relying on the prior two 
  quarters, with residuals confirmed as white noise via the Ljung-Box test
- **Multi-Layer Perceptron (MLP) Neural Network** — a machine learning approach 
  that also identified the two-quarter lag as the primary predictive driver
- **Ensemble model** — combining the ARIMA and MLP forecasts

The MLP outperformed ARIMA on both static RMSE (0.561 vs. 0.721) and rolling 
window RMSE (0.576 vs. 0.611), with the ensemble falling in between. Rolling 
window evaluation showed both models were more stable over time than the 
initial static comparison suggested.

**Key takeaway:** machine learning modestly outperformed traditional statistical 
forecasting for this series, but as a univariate model it's still blind to 
broader macroeconomic forces. Future work should incorporate exogenous 
variables (Federal Funds Rate, unemployment, vehicle sales) via a Vector 
Autoregression model, and consider reframing the problem as directional 
classification (rate up or down) rather than precise point forecasting.

**Data source:** [FRED — Finance Rate on Consumer Installment Loans at 
Commercial Banks, New Autos 60 Month Loan](https://fred.stlouisfed.org/series/RIFLPBCIANM60NM)
