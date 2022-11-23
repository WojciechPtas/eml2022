# 1

## Supervised and Unsupervised learning
In supervised learning, data consists of both inputs and outputs, the goal is to find the function ($\hat{f}$) using the provided input to learn how to estimate outputs values in the future. In unsupervised learning, data consists only of inputs, the goal is to find patterns in the provided data, that should hold for future data as well.

## Prediction and inference

In prediction, the goal is to estimate the value of $Y$, without any interest in the form of $\hat{f}$, it is treated like a black box. We don't need to deeply understand the relationship between the output and the input, our goal is simply to be able to predict the outcome using the predictors. In inference, it is desirable to know as much as possible about the relationship between the input and the output, to understand the nature of this relation.


## Classification and regression

Term regression is used when we want to predict the quantitative output (like wage, number of sales etc.), whereas the classification is a term used when the goal is to predict qualitative output (the stock value is going up or down, applicant gets accepted or rejected etc.). 

## Training and test data

Training data is used to model the data (find the estimator function), whereas test data is used to check the fittness of said function on never seen before data.  

## Parametric and non-parametric method

Parametric methods assume that the number of parameters is fixed, while in non-parametric methods the number of parameters is proportionate to the size of the data. If the parametric method is correct, it produces right estimators with much smaller data set than that is needed in non-parametric methods

# 2

## 1

Required assumptions:
 - $y_0 = f(x_0) +  \epsilon$
 - $E(\epsilon)=0$
 - $\hat{f}(x_0)$ is the estimator function


Proof:

 $MSE=E[(y_0-\hat{f}(x_0))^2]=E[((\hat{f}(x_0)-E(\hat{f}(x_0)))+(E(\hat{f}(x_0))-y_0)))^2]=E[(\hat{f}(x_0)-E(\hat{f}(x_0)))^2]+2E[(\hat{f}(x_0)-E(\hat{f}(x_0)))(E(\hat{f}(x_0))-y_0)]+E[(E(\hat{f}(x_0))-y_0)^2]$

 - $E[(\hat{f}(x_0)-E(\hat{f}(x_0)))^2]$ is the variance of $\hat{f}(x_0)$
 - we substitute the $y_0$ with $f(x_0) +  \epsilon$
 
 $Var(\hat{f}(x_0)) + 2E[(\hat{f}(x_0)-E(\hat{f}(x_0)))(E(\hat{f}(x_0))-f(x_0) -  \epsilon)] + E[(E(\hat{f}(x_0))-f(x_0) - \epsilon)^2]$
 
 Now we need to look at the middle component:
 - $\hat{f}(x_0)-E(\hat{f}(x_0))$ is the devation from the mean for the estimator $\hat{f}$. Its expected value is called the first central moment and is equal to zero

Inspired by [*this*](https://en.wikipedia.org/wiki/Bias%E2%80%93variance_tradeoff) article  

Proof v2:

Required assumptions:

 - $y_0 = f(x_0) +  \epsilon$
 - $f(x_0)$ is not a random variable, it is deterministic so $E[f(x_0)]=f(x_0)$
 - $\epsilon$ is an independent variable
 - $E(\epsilon)=0$, noise is zero-mean, because of it $Var(\epsilon)=E(\epsilon-E(\epsilon))^2=E(\epsilon^2)$
 - $\hat{f}(x_0)$ is the estimator function

$MSE=E[(y_0-\hat{f}(x_0))^2]=E[(f(x_0)+\epsilon - \hat{f}(x_0))^2]$  
$=E[(f(x_0)-E(\hat{f}(x_0))+ \epsilon + E(\hat{f}(x_0))-\hat{f}(x_0))^2]$  
$=E[(f(x_0)-E(\hat{f}(x_0)))^2]+E[\epsilon^2]+E[(E(\hat{f}(x_0))-\hat{f}(x_0))^2]+2E[(f(x_0)-E(\hat{f}(x_0)))*\epsilon]+2E[(f(x_0)-E(\hat{f}(x_0)))(E(\hat{f}(x_0))-\hat{f}(x_0))]+2E[\epsilon*(E(\hat{f}(x_0))-\hat{f}(x_0))]$
Because $Bias$ is not a random value, we can pull it out front   
$=(f(x_0)-E(\hat{f}(x_0)))^2+ Var(\epsilon) + Var(\hat{f}(x_0))+2E[(f(x_0)-E(\hat{f}(x_0)))]*E[\epsilon]+2(f(x_0)-E(\hat{f}(x_0)))*E[(E(\hat{f}(x_0))-\hat{f}(x_0))]+2E[\epsilon]*E[*(E(\hat{f}(x_0))-\hat{f}(x_0))]$  
Because $E[\epsilon]=0$ and $f(x_0)-E(\hat{f}(x_0))=Bias(\hat{f})$ the formula simplifies to:
$=Bias(\hat{f}(x_0))^2 + Var(\epsilon) + Var(\hat{f}(x_0))+2(f(x_0)-E(\hat{f}(x_0)))*E[(E(\hat{f}(x_0))-\hat{f}(x_0))]$
$E(\hat{f}(x_0))-\hat{f}(x_0)$ is called 1st central moment and is always equal zero, so our equation can be simplified further  
$=Bias(\hat{f}(x_0))^2 + Var(\epsilon) + Var(\hat{f}(x_0))+2(f(x_0)-E(\hat{f}(x_0)))*E[0]$  
$=[Bias(\hat{f}(x_0))]^2 + Var(\epsilon) + Var(\hat{f}(x_0))$
Which concludes the proof.

## 2

Reducible error is an error that is produced by the  $\hat{f}$, as it is not a perfect estimate of $f$. We can get rid of this error by fitting a better function to the data, that better resembles the true function. Irreducible error exists, because the $Y$ is also a function of !inherenet! noise ($\epsilon$). We cannot reduce the error, because we cannot separate the $\epsilon$ from the original function.
