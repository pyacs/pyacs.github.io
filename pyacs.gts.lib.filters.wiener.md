---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.filters.wiener
images: {}
path: /pyacs-gts-lib-filters-wiener
title: pyacs.gts.lib.filters.wiener module
---

# pyacs.gts.lib.filters.wiener module

Wiener filter for Gts based on scipy.signal.wiener.

[https://docs.scipy.org/doc/scipy-0.14.0/reference/generated/scipy.signal.wiener.html](https://docs.scipy.org/doc/scipy-0.14.0/reference/generated/scipy.signal.wiener.html)


### pyacs.gts.lib.filters.wiener.wiener(self, in_place=False, verbose=True, my_size=15, noise=None)
returns a filtered time series using scipy.signal.wiener

See documentation for the filter parameters.


* **Parameters**

    
    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series
