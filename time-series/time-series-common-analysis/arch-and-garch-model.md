# ARCH & GARCH model

## ARCH: AutoRegressive Conditional Heteroscedastic model

{% tabs %}
{% tab title="Overview" %}
The conditional expectation of the process is modeled as ARMA process, but with errors that are not white noise
{% endtab %}

{% tab title="Example 1" %}
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

{% tab title="Example 2" %}
This example is given by WQU Econometrics Unit 4



 
{% endtab %}
{% endtabs %}

