
<h1 align="center">
  <br>
	Time-Series-Prediction-using-RNNs
  <br>
</h1>
  <h3 align="center">
    <a href="https://github.com/sLeslau">Shaked Leslau</a> •
    <a href="https://github.com/rishonadaniels">Rishona Daniels</a>

  </h3>
<h3 align="center">Technion 046211: Deep Learning Course Final Project

<h4 align="center">We compare various recurrent neural networks (RNNs) for prediction of dynamic and chaotic time series data. RNNs like long short-term memory (LSTM), gated recurrent unit (GRU) and transformers will be compared with each other and with a novel RNN method called reservoir computing</h4>

<p>See this paper for reference: https://github.com/quantinfo/ng-rc-paper-code/tree/master</hp>

<h4 align="center">
    <a href="https://colab.research.google.com/github/sLeslau/Time-Series-Prediction-using-RNNs"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
</h4>

## Ethics Statement
The stakeholders of this project include weather forecasting stations, organizations trading stocks, etc. 
Weather forecasting stations will be able to use these methods to model and predict the weather forecast using observed time-series data. 
Organizations trading stocks can make decisions based on the predictions of these models 
An ethical consideration is that these models can be used for deterministic chaotic systems. Real-world systems may not be deterministic so care must be taken when designing these models. Also, the reliability of these models must be thoroughly evaluated before deployment in real-world applications especially considering the systems in question are sensitive to initial conditions. 

## Project
A comparison will be made between two standard RNN models namely long-short term memory (LSTM), gated recurrent unit (GRU) as well as a novel RNN model called non-linear vector autoregression (NVAR) also known as reservoir computing. The attention-based transformer model will also be compared on time series data. 

The datasets used are two differential equation systems that exhibit deterministic chaos. 
### Lorenz - 63 system

$$\frac{dx}{dt} = 10(y - x)$$
$$\frac{dy}{dt} = x(28 - z) $$
$$\frac{dx}{dt} = xy - \frac{8z}{3}$$

Here, the lyapunov time is 1.1 time units 

### Mackey-Glass equations

$$\frac{dx}{dt} = \beta \frac{x_\tau}{1 + x_\tau ^ \eta} - \gamma x$$

where $\gamma, \beta, $ and $ \eta > 0$

Here, $\beta, \gamma, \tau, $ and $ \eta $ are real numbers and $x_\tau$ is the value of $x$ at time $(t-\tau)$

Here, $\beta = 0.2, \gamma = 0.1, \eta = 10, $ and $\tau = 17$

When $\tau \geq 17$ the system is chaotic in nature

## Evaluation

## Repository Organization

| File name                                            | Content                                                                                     |
|------------------------------------------------------|---------------------------------------------------------------------------------------------|
| `/notebooks`                                         | Jupyter Notebook implementations of the various models                                      |
| `environment.yml`                                    | Anaconda environment file to install the required dependencies                              |
