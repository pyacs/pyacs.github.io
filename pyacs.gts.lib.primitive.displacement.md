---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.displacement
images: {}
path: /pyacs-gts-lib-primitive-displacement
title: pyacs.gts.lib.primitive.displacement module
---

# pyacs.gts.lib.primitive.displacement module


### pyacs.gts.lib.primitive.displacement.displacement(self, sdate=None, edate=None, window=None, method='median', speriod=[], eperiod=[], rounding='day', verbose=True)
Calculates displacements between two dates or two periods


* **Parameters**

    
    * **sdate** – start date in decimal year


    * **edate** – start date in decimal year


    * **window** – time window in days for searching available dates


    * **method** – method to calculate the position. ‘median’ or ‘mean’. default is ‘median’.


    * **speriod** – period for calculating the start position


    * **eperiod** – period for calculating the end position


    * **rounding** – rounding for dates. Choose among ‘day’,’hour’,’minute’ or ‘second’. default is ‘day’.


    * **verbose** – verbose mode



* **Returns**

    displacement as np.array([dn,de,du,sdn,sde,sdu])
