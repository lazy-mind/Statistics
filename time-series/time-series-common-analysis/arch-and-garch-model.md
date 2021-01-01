# ARCH & GARCH model

## ARCH: AutoRegressive Conditional Heteroscedastic model

{% tabs %}
{% tab title="Overview" %}
The conditional expectation of the process is modeled as ARMA process, but with errors that are not white noise
{% endtab %}

{% tab title="Example" %}
This example is given by WQU Econometrics Unit 4

Assume AR\(1\) process, but with non-white-noise error terms $$u_t$$ :

* $$y_{t}=a_{0}+a_{1} y_{t-1}+u_{t}$$ 

$$u_t$$ has the following structure:

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
{% tab title="First Tab" %}

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
{% endtabs %}



