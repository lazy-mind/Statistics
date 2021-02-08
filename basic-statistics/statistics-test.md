# Statistics Test

**augmented Dickey–Fuller test** \(**ADF**\) tests the [null hypothesis](https://en.wikipedia.org/wiki/Null_hypothesis) that a [unit root](https://en.wikipedia.org/wiki/Unit_root) is present in a [time series](https://en.wikipedia.org/wiki/Time_series) [sample](https://en.wikipedia.org/wiki/Sample_%28statistics%29). The [alternative hypothesis](https://en.wikipedia.org/wiki/Alternative_hypothesis) is different depending on which version of the test is used, but is usually [stationarity](https://en.wikipedia.org/wiki/Stationarity_%28statistics%29) or [trend-stationarity](https://en.wikipedia.org/wiki/Trend-stationary_process).



## Theil’s U

Theil’s U statistic is a relative accuracy measure that compares the forecasted results with the results of forecasting with minimal historical data. It also squares the deviations to give more weight to large errors and to exaggerate errors, which can help eliminate methods with large errors \([Table 2](https://docs.oracle.com/cd/E40248_01/epm.1112/cb_statistical/ch07s02s03s04.html#terms1085662)\).

$$U=\left\{ sqrt\frac{\sum_{t=1}^{n-1}\left(\frac{\hat{Y}_{t+1}-Y_{t+1}}{Y_{t}}\right)^{2}}{\sum_{t=1}^{n-1}\left(\frac{Y_{t+1}-Y_{t}}{Y_{t}}\right)^{2}}\right.$$ 

| Theil’s U Statistic | Interpretation |
| :--- | :--- |
| Less than 1 | The forecasting technique is better than guessing. |
| 1 | The forecasting technique is about as good as guessing. |
| More than 1 | The forecasting technique is worse than guessing. |



