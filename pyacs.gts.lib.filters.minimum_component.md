---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.filters.minimum_component
images: {}
path: /pyacs-gts-lib-filters-minimum-component
title: pyacs.gts.lib.filters.minimum_component module
---

# pyacs.gts.lib.filters.minimum_component module

Minimum component filter for Gts.


### pyacs.gts.lib.filters.minimum_component.minimum_component(self, mask_period=[], p=1, fcut=None, Q=None, in_place=False, verbose=True)
Minimum component filtering for Gts.

Minimum component filtering is useful for determining the background
component of a signal in the presence of spikes


* **Parameters**

    
    * **mask_periods** – periods (list or list of lists) which should be ignored for smoothing


    * **p** – integer (optional). polynomial degree to be used for the fit (default = 1)


    * **fcut** – float (optional). the cutoff frequency for the low-pass filter.  Default value is f_nyq / sqrt(N)


    * **Q** – float (optional). the strength of the low-pass filter.  Larger Q means a steeper cutoff. default value is 0.1 \* fcut


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



* **Note**


This code follows the procedure explained in the book
“Practical Statistics for Astronomers” by Wall & Jenkins book, as
well as in Wall, J, A&A 122:371, 1997
