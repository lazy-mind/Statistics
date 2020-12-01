# Time Series with Leading Indicators

## Reference:

* [https://www.vosesoftware.com/riskwiki/Timeseriesmodelswithleadingindicators.php](https://www.vosesoftware.com/riskwiki/Timeseriesmodelswithleadingindicators.php)

## Key Steps:

1. Define causal relationship
2. Define quantitative nature

## Theory Support

* [Granger Causality](https://en.wikipedia.org/wiki/Granger_causality)
  * Variable X that evolves over time _`Granger-causes`_ another evolving variable Y, if predictions of the value of Y based on its own past values and on the past values of X, are better than predictions of Y based only on Y's own past values.
  * $$\mathbb{P}[Y(t+1) \in A \mid \mathcal{I}(t)] \neq \mathbb{P}\left[Y(t+1) \in A \mid \mathcal{I}_{-X}(t)\right]$$ 
  * $$y_{t}=a_{0}+\sum_{j=1}^{k} b_{j} y_{t-j}+\epsilon_{t}$$ 
  * $$y_{t}=a_{0}+\sum_{j=1}^{k} b_{j} y_{t-j}+\sum_{l=1}^{m} c_{l} z_{t-l}+\epsilon_{t}$$ 

## Papers

* Academic Study
  * [Learning Leading Indicators for Time Series Predictions.](https://arxiv.org/pdf/1507.01978.pdf)
  * [Learning Predictive Leading Indicators for Forecasting Time Series Systems with Unknown Clusters of Forecast Tasks.](http://proceedings.mlr.press/v77/gregorova17a/gregorova17a.pdf)
* Industry Study
  * [Understanding Automatic Time Series Modeling and Forecasting: Case Studies of Forecasting Real GDP, the Unemployment Rate, and the Impact of Leading Economic Indicators](https://isf.forecasters.org/wp-content/uploads/gravity_forms/2-dd30f7ae09136fa695c552259bdb3f99/2019/06/Understanding-Automatic-Time-Series-Modeling-and-Forecasting-06132019.pdf).



## Application Samples:

* \*\*\*\*[**Time Series Forecasting using Granger’s Causality and Vector Auto-regressive Model**](https://towardsdatascience.com/granger-causality-and-vector-auto-regressive-model-for-time-series-forecasting-3226a64889a6)\*\*\*\*
* \*\*\*\*[**Using Granger Causality Test to Know If One Time Series Is Impacting in Predicting Another?**](https://medium.com/swlh/using-granger-causality-test-to-know-if-one-time-series-is-impacting-in-predicting-another-6285b9fd2d1c)\*\*\*\*

