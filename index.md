---
title       : MyPresentation
subtitle    : So hard
author      : JLVZ
job         : Majadahonda
framework   : html5slides       # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

---

## VaR and TVaR sample estimation for compound distributions

1. VaR and TVaR risk measures.
2. Compound distributions as risk models in insurance (1), (2). 
3. Estimation of  VaR and TVaR for compound distributions.
4. Functionning of our shiny app.


--- .class #id 

## VaR and TVaR risk measures.
Let be $X\ge0$ a random variable representing a loss.
Given its cumulative distribution function (cdf) $F_X(x)$
the Value at Risk (VaR) and Tail Value at risk (TVaR) at some probability level $p\in [0,1]$ are respectively$$VaR[X,p]=F_X^{-1}(p)$$ 
$$TVaR[X,p]=\frac{1}{1-p}\int_{p}^{1}VaR[X,\xi]d\xi $$
For a given $p\in [0,1]$ both functions associate to the cdf $F_X(x)$ real numbers representing   the loss (in monetary units) at the $p$-level. In that sense thay are measuring the risk associated to the r.v. (loss) $X$. 
That's why they are called "RISK MEASURES"




--- .class #id


## Compound distributions as risk models in insurance (1)
Now suppose that the r.v. $X$ is representing the loss in a one year general insurance policy. 
How can we model the future random loss associated to that contract?
There will clearly exist two random sources: 

1. The random claims number of the policy:

  Let be $N\in \{0,1,2,...\}$ the random variable representing the claim number during the year.
  
2. The severities of the policy claims:

  Let $\{X_i\}_{i=1}^{\infty}$ be a sequence of i.i.d. r.v. ($X_i\ge0$) representing the claims severities.
  
3. Assume that the r.v. $N$ and $\{X_i\}_{i=1}^{\infty}$ are mutually independent.


---.class #id


## Compound distributions as risk models in insurance (1)
Now suppose that the r.v. $X$ is representing the loss in a one year general insurance policy. 
How can we model the future random loss associated to that contract?
There will clearly exist two random sources: 

1. The random claims number of the policy:

  Let be $N\in \{0,1,2,...\}$ the random variable representing the claim number during the year.
  
2. The severities of the policy claims:

  Let $\{X_i\}_{i=1}^{\infty}$ be a sequence of i.i.d. r.v. ($X_i\ge0$) representing the claims severities.
  
3. Assume that the r.v. $N$ and $\{X_i\}_{i=1}^{\infty}$ are mutually independent.


---.class #id

## Compound distributions as risk models in insurance (2)
Then the total loss of the policy is a compound random variable:

  $S=\sum_{k=1}^N X_{i}$   if   $N>0$   ,   $S=0$  if  $N=0$
  
Now suppose $p_n=P\{N=n\}$ and $V_X(x)$ are respectively the cdf's for $N$ and $X$.

The cdf of the total loss is a compound distribution 
$$F_S(s)=P\{S\le s\}=\sum_{n=0}^{\infty} p_n V_X^{*(n)}(s)$$

where $^*(n)$ stands for the n-fold convolution product.

--- .class #id

## Estimation of  VaR and TVaR for compound distributions.

Now looking to the symbolic formula for a compound cdf it is clear that it is not that easy to handle. Probabilities or quantiles calculations are in general hard to achieve. There are in fact different approaches to overcome these issues: recursive algorithms, approximations, fast Fourier transform, etc...

In our Shiny App we illustrate the estimation of VaR and TVaR by means of simulation and sample estimation. 

We fix the $p_n$ distribution as a Poisson $P(\lambda)$ distribution, and the $X$ as Gamma$(\alpha,\beta)$.

User has to choose the three parameters: $\lambda >0$,$\alpha>$,$\beta>0$, the number of simulations for the compound variable $S$, the probability level $p\in [0.05,0.995]$ and a simulation seed.

--- .class #id

## Estimation of  VaR and TVaR for compound distributions (2).

Our shiny App performs the following steps:

1. Simulate a sample of total losses $S$.

2. Calculate the corresponding samples estimates for VaR and TVaR.

3. Plot the sample histogram together with the two estimated risk measures values.

--- .class #id

## This is the end

Thank you for reading these slides!




