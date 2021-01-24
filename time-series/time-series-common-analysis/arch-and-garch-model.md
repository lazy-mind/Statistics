# ARCH & GARCH model

## ARCH: AutoRegressive Conditional Heteroscedastic model

{% tabs %}
{% tab title="Overview" %}
## Definition:

* It is used to describe periods of volatility in the process
* "Heteroscedasitc": means that not all characteristics are the same at all time
* "Conditional Heteroscedastic": means that at different timeframe the volatility is different.
* "AutoRegressive Conditional Heteroscedastic": menas that the volatility is an autoregressive process, being determined by the past values
* In another interpretation, we can say that: The conditional expectation of the process is modeled as ARMA process, but with errors that are not white noise

## Real-life Meaning:

* Imagine a stock market, at different years the market tends to be more volatile or less volatile.
{% endtab %}

{% tab title="Example" %}
This example is given by WQU Econometrics Unit 4

Assume AR\(1\) process, but with non-white-noise error terms $$u_t$$ :

* $$y_{t}=a_{0}+a_{1} y_{t-1}+u_{t}$$ 



As we said in the overview, this error term can be different at different timepoint, and the its variance \(its volatility, which cause a non-constant volatility in the process\) should be modeled as an auto-regressive process. 

That means we want: $$Var(\mu_t) = \sigma_t^2 = \alpha_0 + \alpha_1 \sigma_{t-1}^2$$ . Which models the variance of error as auto-regressive process.

To let the variance has such feature, the error process should be modelled as: $$u_{t}=\varepsilon_{t} \sqrt{\omega+\alpha_{1} u_{t-1}^{2}}$$ . 



The error term: "$$u_t$$"  has the following structure:

* Expectation remains 0: $$\mathbb{E}\left(u_{t}\right)=\mathbb{E}_{t-1}\left(u_{t}\right)=0$$ 
* Errors are uncorrelated overtime: $$\mathbb{E}\left(u_{t} u_{t-s}\right)=0 \forall s>0$$ 
* Conditional variance can be auto-correlated: $$\mathbb{E}_{t}\left(u_{t}^{2}\right)=\sigma_{t}^{2}$$ 



We need to model the $$\sigma_t^2$$ as it is not observable \(it is the variance of the error!\). There are many ways to model this variance, and they have respective conditions for stationarity to hold

* The easiest way is to model it as **ARCH\(1\)**
  * $$u_{t}=\varepsilon_{t} \sqrt{\omega+\alpha_{1} u_{t-1}^{2}}$$ , $$\varepsilon_t \text{ is a white noise independent from }u_t$$ 
* A more sophisticated extension will be **ARCH\(p\)**:
  * $$u_{t}=\varepsilon_{t} \sqrt{\omega+\alpha_{1} u_{t-1}^{2}+\cdots+\alpha_{p} u_{t-p}^{2}}$$
* Another extension will be **ARCH\(p, 1\)**:
  * $$\begin{array}{c} u_{t}=\varepsilon_{t} \sqrt{h_{t}} \\ \\ h_{t}=\omega+\sum_{i=1}^{p} \alpha_{i} u_{t-i}^{2}+\sum_{j=1}^{q} \beta_{j} h_{t-j} \end{array}$$ 



We study the easiest one, ARCH\(1\), and we can do the following analysis:

* period $$t-1$$ conditioanl variance of $$u_t$$ will be:
  * $$\begin{aligned} \mathbb{E}_{t-1}\left(u_{t}^{2}\right) &=\mathbb{E}_{t-1}\left(\varepsilon_{t} \sqrt{\omega+\alpha_{1} u_{t-1}^{2}}\right)^{2} \\ &=\sigma_{\varepsilon}^{2}\left(\omega+\alpha_{1} \mathbb{E}_{t-1}\left(u_{t-1}^{2}\right)\right) \\ &=\omega+\alpha_{1} u_{t-1}^{2} \end{aligned}$$ 
  * which is an AR\(1\) process in $$u_t^2$$ 
  * and if $$\alpha_1 <1$$ , it is a stationary process
* using the definition of stationarity: $$\mathbb{E}\left(u_{t}^{2}\right)=\mathbb{E}\left(u_{t-1}^{2}\right)$$ , we have
  * $$\begin{aligned} \mathbb{E}\left(u_{t}^{2}\right) &=\mathbb{E}\left(\varepsilon_{t} \sqrt{\omega+\alpha_{1} u_{t-1}^{2}}\right)^{2} \\ &=\omega+\alpha_{1} \mathbb{E}\left(u_{t-1}^{2}\right) \\ &=\frac{\omega}{1-\alpha_{1}} \end{aligned}$$ 
{% endtab %}

{% tab title="Limitation" %}
1. The model assumes symmetric effects: whether a shock to the process is positive or negative, the impact on the conditional variance is the same. This is not representative for financial series - negative shocks tend to be more destabilizing to the variability of the returns on a financial asset than positive shocks. Consider what happened in the Global Financial Crisis of 2008 . The EGARCH model mentioned below is a generalization built to deal with this weakness.
2. ARCH models allowing only AR properties in the conditional variance process tend to predict slow mean reversion in the conditional variance. In practice, there can be sharp spikes in volatility that vanish quickly.
3. The ARCH model struggles to deal with excess kurtosis \(relative to normal distributions\) due to fundamental mathematical constraints that must hold for the derivations to be well defined. This can be rectified somewhat by using distributions other than the normal ones \(with fatter tails and more kurtosis\).
4. The ARCH model allows only the shock to the conditional expectation to feed to persistence in the conditional variance but does not allow changes in the conditional variance to affect the conditional expectation. In practice, we may expect the expected return on an asset to be depressed in periods of high volatility. The GARCH-M process is built to allow this feedback.
5. The model imposes a specific, mechanical process that generates the conditional variance time path. It does not explain why the conditional variance follows this process. For the skeptical financial engineer, this is not too troublesome if the interest is in near future projections rather than fundamental analysis. For the long run investor, however, this is not desirable.
{% endtab %}

{% tab title="MLE of GARCH" %}

{% endtab %}
{% endtabs %}

## GARCH: Generalized ARCH

{% tabs %}
{% tab title="Example" %}
Let's take a look at example GARCH\(1,1\)

* $$\sigma_{t}^{2}=\omega+\alpha \varepsilon_{t-1}^{2}+\beta \sigma_{t-1}^{2}$$ 

Interpretation of the parameters:

* $$\omega, \alpha \text { and } \beta \text { must be positive with } \alpha+\beta<1$$ 
* $$\alpha$$ is a reaction parameter. High $$\alpha$$ is generally associated with spiky or nervous market while low $$\alpha$$ indicates stable market. 
  * Alexander \(2008\) considers that for daily data used in GARCH model, $$\alpha$$ generally ranges from 0.05 \(stable market\) to 0.10 for a spiky one.
* $$\beta$$ indicates volatility persistence \(how much from past volatility is transferred into current volatility\). High $$\beta$$ means high persistency and therefore volatility clustering appears. 
  * $$\beta$$ generally takes values from 0.85 to 0.98 for daily data used in the model according to Alexander \(2008\).
* Low $$\alpha$$ values are associated with high $$\beta$$ 
* high $$\alpha$$ is connected to low $$\beta$$ 
* $$\frac{\omega}{1-\alpha-\beta}->\text { unconditional variance }$$ 
{% endtab %}

{% tab title="First Tab" %}
### TGARCH & EGARCH

**T-GARCH \(Threshold-GARCH\)**: A piece of "bad news", or a negative return, such as a drop in the stock price, reduces the value of equity relative to the fixed value of debt of that firm according to Enders \(2014\). The opposite effect will also be present - an increase in the stock price reduces leverage and risk.

* $$h_{t}=\omega+\alpha_{1} u_{t-1}^{2}+\gamma_{1} d_{t-1} u_{t-1}^{2}+\beta_{1} h_{t-1}$$ 
* $$d_{t-1} = 0, \text{ if } \varepsilon_{t-1} >0.  \text{ positive shock will not bring much impact}$$ 
* $$d_{t-1} = 1, \text{ if } \varepsilon_{t-1} <0.  \text{ negative shock will have larger impact}$$ 

**EGARCH:** model employs a logarithmic transformation to $h_{t}$ to ensure positive variances \(in all the other models, all the estimated coefficients need to be positive, which is not the case here\) as well as working in the levels of the residuals \(not their squares\) and additionally, standardizing by their standard deviation $\sqrt{h_{t}}$.

* $$\ln \left(h_{t}\right)=\omega+\alpha_{1} \frac{u_{t-1}}{\sqrt{h_{t-1}}}+\gamma_{1}\left|\frac{u_{t-1}}{\sqrt{h_{t-1}}}\right|+\beta_{1} \ln \left(h_{t-1}\right)$$ 
* \text { if } u_{t-1}&gt;0 \text { its impact on } \ln \left\(h_{t}\right\) \text { is } \alpha_{1}+\gamma_{1}
* \text { If } u\_{t-1}&lt;0 \text { its impact is } \ln \left\(h_{t}\right\) \text { is }-\alpha_{1}+\gamma\_{1}

### IGARCH
{% endtab %}

{% tab title="MLE of Linear Regression" %}
For a normally distributed $$\left\{\varepsilon_{t}\right\}$$ , the MLE is:

* $$\ln L=-\frac{T}{2} \ln (2 \pi)-\frac{T}{2} \ln \sigma^{2}-\frac{1}{2 \sigma^{2}} \sum_{t=1}^{T} \varepsilon_{t}^{2}$$ 

Now that we have a model describing how $$\left\{\varepsilon_{t}\right\}$$ is generated, we can plug it in:

* $$\varepsilon_{t}=y_{t}-\beta x_{t}$$ 
* $$\ln L=-\frac{T}{2} \ln (2 \pi)-\frac{T}{2} \ln \sigma^{2}-\frac{1}{2 \sigma^{2}} \sum_{t=1}^{T}\left(y_{t}-\beta x_{t}\right)^{2}$$ 

And the so that we can estimate the model parameters based on sample data:

* $$\begin{array}{c} \hat{\sigma}^{2}=\frac{\sum \varepsilon_{t}^{2}}{T} \\ \\  \hat{\beta}=\frac{\sum x_{t} y_{t}}{\sum x_{t}^{2}} \end{array}$$ 
{% endtab %}

{% tab title="MLE of GARCH" %}
Now for the GARCH, the distribution of $$\left\{\varepsilon_{t}\right\}$$ is no longer normal, but:

* $$\varepsilon_{t}=v_{t}\left(h_{t}\right)^{0.5} \text { (the conditional variance is not constant) }$$ 

And the MLE estimator will become:

* $$L=\prod_{t=1}^{T}\left(\frac{1}{\sqrt{2 \pi h_{t}}}\right) \exp \left(\frac{-\varepsilon_{t}^{2}}{2 h_{t}}\right)$$ 
* $$\ln L=-\frac{T}{2} \ln (2 \pi)-0.5 \sum_{t=1}^{T} \ln (h_{t})-0.5 \sum_{t=1}^{T}\left(\frac{\varepsilon_{t}^{2}}{h_{t}}\right).$$ 
* $$\varepsilon_{t}=y_{t}-\beta x_{t}$$ 
* For ARCH\(1\), the conditional variance is: $$h_{t}=a_{0}+a_{1} \varepsilon_{t-1}^{2}$$ 

Then the MLE estimator is:

* $$\ln \mathrm{L}=-\frac{T-1}{2} \ln (2 \pi)-0.5 \sum_{t=2}^{T}\left(\ln\alpha_{0}+ \alpha_{1} \varepsilon_{t-1}^{2}\right)-0.5 \sum_{t=2}^{T}\left(\frac{y_{t}-\beta x_{t}}{\alpha_{0}+\alpha_{1} \varepsilon_{t-1}^{2}}\right)$$

The problem of solving the estimator is:

1. The initial observation is lost since$$\text {  } \varepsilon_{0} $$ is outside the sample
2. There are no simple solutions to the first-order conditions for a maximum
3. Computers are able to select parameter values that maximize log likelihood
{% endtab %}

{% tab title="GARCH-M" %}
The GARCH-in-mean or GARCH-M model addresses the limitations of standard ARCH / GARCH models which do not allow the realization of the conditional variance process to affect the conditional expectation. It can be established that during a financial crisis, the returns on many assets are lower than in more tranquil times. Alternatively, an asset that is systematically riskier than another must offer a higher return to be invested in.

GARCH\(1,1\)-M: $$\begin{array}{c} r_{t}=\mu+c \sigma_{t-1}^{2}+u_{t} \\ \\ u_{t}=\varepsilon_{t} \sqrt{h_{t}} \\ \\ h_{t}=\omega+\alpha_{1} u_{t-1}^{2}+\beta_{1} h_{t-1} \end{array}$$ 

If $c$ is significantly positive, it can be considered a "risk premium" for the asset in times when it is more volatile. Other alternatives are to use just the conditional standard deviation $\sigma\_{t}$ or the log of the variance in the mean equation.
{% endtab %}

{% tab title="" %}

{% endtab %}
{% endtabs %}

## Kalman Filter

$$x_{t}=F_{t} \times x_{t-1}+B_{t} \times u_{t}+w_{t}$$ 

* $$x_{t}$$ - state vector containing the terms of interest for the system \(volatility of returns\) at time $$t$$ 
* $$u_t$$ the vector containing any control inputs \(steering angle for example at physics\) 
* $$f_{t}$$ - state transition matrix which applies the effect of each system state parameter at time $$t-1$$ on the system state at time $$t$$ \(example the position and velocity at time $$t-1$$ both affect the position at time $$t$$ \)
* $$b_{t}$$ - the control-input matrix which applies the effect of each control input parameter in the vector $$u_t$$ on the state vector 
* $$w_t $$ - the vector containing the process noise terms for each parameter in the state vector. $$w_{t} \sim N\left(0, Q_{t}\right)$$ 

An observation \(or measurement\) $$z_{t}$$ _of the true state_ $$x_t$$  is made according to:

$$z_{t}=H_{t} x_{t}+v_{t}$$ 

* where $$H_t$$ _is the observation model which maps the true state space into the observed space and_ $$v_t$$ is the observation noise which is assumed to be zero-mean Gaussian white noise with covariance $$R_t$$. $$v_{t} \sim N\left(0, R_{t}\right)$$ 

