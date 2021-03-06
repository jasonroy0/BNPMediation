# BNPMediation
Bayesian Nonparametric Method for Mediation. This package is the software implementation of the methods in Kim et al. (2016) "A framework for Bayesian nonparametric inference for causal effects of mediation", Biometrics.

To install this package:
```
library(devtools)
install_github("lit777/BNPMediation")
library(BNPMediation)
```
Before run the function:
- First, fit the observed data models for both treatments using DPdensity (from DPpackage).
```
install.packages("DPpackage")
library(DPpackage)

fit1 <- DPdensity(y=w1,prior=prior,mcmc=mcmc,state=state,status=TRUE, na.action=na.omit)
fit0 <- DPdensity(y=w0,prior=prior,mcmc=mcmc,state=state,status=TRUE, na.action=na.omit)
```
To obtain the posterior means and credible intervals of the effects:
```
model<-bnpmediation(fit1, fit0, q=5, NN = 10, n1, n0, extra.thin = 0)
```
For more details, type
```
help(bnpmediation)
```
To obtain the posterior means and credible intervals of the conditional effects:
```
model<-bnpconmediation(fit1, fit0, q=5, NN=10, n1, n0, extra.thin=0, cond.values=c(x1,x2), col.values=c(1,2))
```
For more details, type
```
help(bnpconmediation)
```
To obtain posterior samples of the potential outcomes, E[Y1] and E[Y0]:
```
OutSamples(fit1, fit0, q=2)
```
For more details, type
```
help(OutSamples)
```
To obtain the posterior plots of the effects:
```
PlotEffects(model)
```
