
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
### Introduction
Any system that evolves with time is a dynamical system. All real-world processes are dynamical systems and it is useful to predict the trajectory of these systems using mathematical models. For example, weather prediction, stock-market prediction, physiological systems, etc. However, modeling of dynamical systems is complicated because of the large number of parameters that affect the trajectory. Also, these systems are very sensitive to the initial conditions and a small change in the initial conditions can have a dramatic impact on the trajectory of the output.  Various machine learning approaches are used to generate models of dynamical systems using observed data however, these approaches are data hungry, require long observation times and consume large computational resources. 
A comparison will be made between two standard RNN models namely long-short term memory (LSTM), gated recurrent unit (GRU) as well as a novel RNN model called non-linear vector autoregression (NVAR) also known as reservoir computing. The attention-based transformer model will also be compared on time series data. 

The datasets used are two differential equation systems that exhibit deterministic chaos. 
#### Lorenz - 63 system

$$\frac{dx}{dt} = 10(y - x)$$
$$\frac{dy}{dt} = x(28 - z) $$
$$\frac{dx}{dt} = xy - \frac{8z}{3}$$

Here, the lyapunov time is 1.1 time units 

#### Mackey-Glass equations

$$\frac{dx}{dt} = \beta \frac{x_\tau}{1 + x_\tau ^ \eta} - \gamma x$$

where $\gamma, \beta, \eta > 0$

Here, $\beta, \gamma, \tau, \eta$ are real numbers and $x_\tau$ is the value of $x$ at time $(t-\tau)$

Here, $\beta = 0.2, \gamma = 0.1, \eta = 10, \tau = 17$

When $\tau \geq 17$ the system is chaotic in nature

### Evaluation and Results
We used PyTorch toolbox to implement the LSTM, GRU, and transformer. For NVAR, we
using the implementation provided. They have implemented NVAR using Numpy and
their implementations are in their GitHub repository. To provide a valid comparison, we
needed to maintain consistency across the data sets, models, and loss functions. We trained
each model on the generated Lorenz 63’ dataset which we normalized, and tested it on the
continuation of the same sequence.
When tuning the hyperparameters, we found that the number of epochs had the greatest
effect on the outcome. Additionally, we found that increasing the complexity of the model
did not improve the result as expected. We surmise that this is because the dataset was
relatively small (on the order of 800 – 2000 samples), and so the model quickly began to
overfit, neutralizing any benefits from a highly complex model. Additionally, we found
that the results of each of the models varied greatly across training runs, even when the
hyperparameters were left constant. The model that varied the most was the transformer. We
believe this is because it is very data hungry, and our training data was simply too small to
properly train on. Additionally, the nature of the chaotic timeseries makes it very complex to
learn, and small differences in initial conditions can drastically change the results.

We see the results of the models on the Lorenz '63 dataset below
#### LSTM
![image](https://github.com/sLeslau/Time-Series-Prediction-using-RNNs/assets/64160899/bfd46df1-8d9a-44a1-948f-de81312c47de)

#### GRU
![image](https://github.com/sLeslau/Time-Series-Prediction-using-RNNs/assets/64160899/3695b069-b327-4f04-807c-26676dea80f8)

#### Transformer
![image](https://github.com/sLeslau/Time-Series-Prediction-using-RNNs/assets/64160899/38e0a22a-40fc-4a4d-b931-1e1858cbb2d1)

#### RC-NVAR
![image](https://github.com/sLeslau/Time-Series-Prediction-using-RNNs/assets/64160899/761987db-eebf-4fc3-8f3a-115fc906f4e4)

### Repository Organization

| File name                                            | Content                                                                                     |
|------------------------------------------------------|---------------------------------------------------------------------------------------------|
| `/notebooks`                                         | Jupyter Notebook implementations of the various models                                      |
| `environment.yml`                                    | Anaconda environment file to install the required dependencies                              |
