---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.filters.total_variation
images: {}
path: /pyacs-gts-lib-filters-total-variation
title: pyacs.gts.lib.filters.total_variation module
---

# pyacs.gts.lib.filters.total_variation module

Total variation filters from [https://github.com/albarji/proxTV](https://github.com/albarji/proxTV)
Total variation filters are useful to preserve edges in a signal (edge filter).


### pyacs.gts.lib.filters.total_variation.edge(self, lbda, in_place=False, verbose=True)
Edge Gts filter using a L1 total variation filter.
The signal is assumed to be piecewise constant.


* **Parameters**

    
    * **lbda** – lambda parameter


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



* **Reference**

    [https://github.com/albarji/proxTV](https://github.com/albarji/proxTV)



### pyacs.gts.lib.filters.total_variation.edge_l2(self, lbda, in_place=False, verbose=True)
Gts filter using a L2 total variation filter.
The signal is assumed to be detrended.


* **Parameters**

    
    * **lbda** – lambda parameter


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



* **Reference**

    [https://github.com/albarji/proxTV](https://github.com/albarji/proxTV)
