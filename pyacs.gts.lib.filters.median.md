---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.filters.median
images: {}
path: /pyacs-gts-lib-filters-median
title: pyacs.gts.lib.filters.median module
---

# pyacs.gts.lib.filters.median module

Median filter for Gts based on scipy.signal.medfilt.


### pyacs.gts.lib.filters.median.median_filter(self, n, in_place=False, verbose=True)
returns a filtered time series using scipy.signal.medfilt


* **Parameters**

    
    * **n** – size of the median filter window (must be odd)


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



* **Note**

    the filter is applied to .data and .data_xyz is set to None
