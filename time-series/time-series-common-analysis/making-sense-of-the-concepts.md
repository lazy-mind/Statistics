# Making sense of the concepts

* Stationary:
  * A time series is considered stationary if the values never drift far away from their initial value. A variable that has a finite mean and variance is considered covariance stationary. Stationary time series variables tend to return to their mean after a period of time \(mean- reversion\), and their deviations from the mean tend to be constant.
  * We want time-series to be stationary \(no trend\) because we want to eliminate un-necessary correlation in our analysis.
  * If 2 time series both have upward trend, then our analysis will show they are having high correlation while they might have no relationship at all.
  * Most financial and macroeconomic variables are not stationary, but in some cases the linear combination of some variables is stationary \(cointegration\). In this case, the variables are said to share the same stochastic trend.

