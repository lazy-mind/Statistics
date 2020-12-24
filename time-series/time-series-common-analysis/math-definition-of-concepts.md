# Math Definition of concepts

{% tabs %}
{% tab title="White Noise" %}
$$\begin{aligned} &\left\{\varepsilon_{t}\right\} \text { is a white-noise process if the following conditions are satisfied: }\\ &E\left(\varepsilon_{t}\right)=E\left(\varepsilon_{t-1}\right)=\ldots=0\\ &E\left(\varepsilon_{t}^{2}\right)=E\left(\varepsilon_{t-1}^{2}\right)=\ldots=\sigma^{2} \operatorname{or} \operatorname{var}\left(\varepsilon_{t}\right)=\operatorname{var}\left(\varepsilon_{t-1}\right)=\ldots=\sigma^{2}\\ &E\left(\varepsilon_{t} \varepsilon_{t-s}\right)=E\left(\varepsilon_{t-j} \varepsilon_{t-j-s}\right)=0 \text { for all j and } s \text { or }\\ &\operatorname{cov}\left(\varepsilon_{t}, \varepsilon_{t-s}\right)=\operatorname{cov}\left(\varepsilon_{t-j}, \varepsilon_{t-j-s}\right)=0 \end{aligned}$$ 
{% endtab %}

{% tab title="Covariance Stationary" %}
$$\begin{aligned} &\left\{y_{t}\right\} \text { is covariance stationary if: }\\ &E\left(y_{t}\right)=E\left(y_{t-s}\right)=\mu\\ &E\left[\left(y_{t}-\mu\right)^{2}\right]=E\left[\left(y_{t-s}-\mu\right)^{2}\right]=\sigma_{y}^{2} \quad\left[\operatorname{var}\left(y_{t}\right)=\operatorname{var}\left(y_{t-s}\right)=\sigma_{y}^{2}\right]\\ &E\left[\left(y_{t}-\mu\right)\left(y_{t-s}-\mu\right)\right]=E\left[\left(y_{t-j}-\mu\right)\left(y_{t-j-s}-\mu\right)\right]=\gamma_{s} \end{aligned}$$ 

$$\text{ where $\mu, \sigma_{y}^{2}$ and $\gamma_{s}$ are all constants }$$ 

$$\rho_{s}=\frac{\gamma_{s}}{\gamma_{0}} \text{ autocorrelation between $y_{t}$ and $y_{t-s}$}$$ 

$$\begin{array}{l} \phi_{11}=\rho_{1}-\text { partial autocorrelation } \\ \phi_{22}=\left(\rho_{2}-\rho_{1}^{2}\right) /\left(1-\rho_{1}^{2}\right) \text { - partial autocorrelation } \\ \qquad \phi_{s s}=\frac{\rho_{s}-\sum_{j=1}^{s-1} \phi_{s-1, j} \rho_{s-j}}{1-\sum_{j=1}^{s-1} \phi_{s-1, j} \rho_{j}} \text { - partial autocorrelation } \end{array}$$ 

$$\begin{array}{l} s=3,4,5 \ldots \\ \phi_{s j}=\phi_{s-1, j}-\phi_{s s} \phi_{s-1, s-j} \\ j=1,2,3, \ldots, s-1 \end{array}$$ 

 
{% endtab %}
{% endtabs %}

