---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.filters.piecewise_linear
images: {}
path: /pyacs-gts-lib-filters-piecewise-linear
title: pyacs.gts.lib.filters.piecewise_linear module
---

# pyacs.gts.lib.filters.piecewise_linear module

Piecewise linear approximation of time series. 
Based on [https://pypi.org/project/pwlf](https://pypi.org/project/pwlf).


### pyacs.gts.lib.filters.piecewise_linear.pwlf(self, component, n, in_place=False, verbose=False, output=False)
Perform a piecewise approximation of a time series. Since it the routine is 1D, the component E,N, or U needs to be specified.


* **Parameters**

    
    * **component** – component used for the decomposition. Must be ‘E’,’N’ or ‘U’


    * **n** – number of segments


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Output**

    if False, the predicted time series is returned. If True, then a list of dates is returned.
