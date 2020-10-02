---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.robustestimators
images: {}
path: /pyacs-lib-robustestimators
title: pyacs.lib.robustestimators module
---

# pyacs.lib.robustestimators module

RobustEstimators.py includes a number of robust estimators
to solve linear problems.


### exception pyacs.lib.robustestimators.Error()
Bases: `Exception`

Base class for exceptions in module robustestimators.py


### exception pyacs.lib.robustestimators.UnboundedFunctionError()
Bases: `Exception`

Exception raised for unbounded objective function.


### pyacs.lib.robustestimators.Dikin(A, y, W, eps=0.003)
L1-norm estimation of parameters x using the Dikin’s method
using Linear optimization in linear model  y=Ax+e


* **Parameters**

    
    * **A** – Model matrix


    * **y** – observed values (observation vector)


    * **W** – Weight matrix of observables (of DIAGONAL type)


    * **eps** – small value for iteration (default: eps = 1e-6)


:return : x,e: vector of estimated parameters and residuals


* **Note**

    translated from Matlab code kindly provided by Amir Khodabandeh june.2009


reference:Recursive Algorithm for L1 Norm Estimation in Linear Models,
A. Khodabandeh and A. R. Amiri-Simkooei, JOURNAL OF SURVEYING ENGINEERING ASCE / FEBRUARY 2011 / 1
doi:10.1061/ASCESU.1943-5428.0000031
Translated to python from Matlab original by J.-M. Nocquet July 2011


### pyacs.lib.robustestimators.Dik_m(c, A, b, er)
subject:solve the standard form of linear programming by affine/Dikin’s
method(“an interior point method”) 
minimize z=c’

```
*
```

x; subject to Ax=b;
input:(c):coefficients of objective function(z) as n-vector(hint:a column
vector)
(A):matrix of constraint set with size m\*n
(b):m-vector of constraint set 
(er):maximum discrepancy between two iteration.(“stopping criterion”)
output:(X):unknown variables
(z):optimal value of objective function
(D):Centering transformer “D”(a diagonal matrix)
Amir khodabandeh Oct.2008
