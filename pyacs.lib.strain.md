---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.strain
images: {}
path: /pyacs-lib-strain
title: pyacs.lib.strain module
---

# pyacs.lib.strain module

Strain rate calculation library


### pyacs.lib.strain.vgrad(X, Y, VE, VN, SVE=None, SVN=None, CVEN=None, CODE=None, method='WLS', verbose=False)
Linear estimates of a horizontal velocity gradient


* **Parameters**

    
    * **X****,****Y** – 1D numpy array of longitudes and latitudes


    * **VE****,****VN** – 1D numpy array of east and north velocity. Unit is assummed to be mm/yr


    * **SVE****,****SVN****,****CVEN** – 1D numpy array of east and north velocity standard deviation (mm/yr) and correlation.


    * **CODE** – 1D numpy of string with site codes


    * **method** – estimator in ‘L1’,’WLS’ (default: weighted least-squares ‘WLS’)



* **Returns**

    DV, the velocity gradient tensor as a 2x2 2D-numpy array and a 2-columns (East and North) residuals 2D numpy array
