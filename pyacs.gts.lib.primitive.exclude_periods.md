---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.exclude_periods
images: {}
path: /pyacs-gts-lib-primitive-exclude-periods
title: pyacs.gts.lib.primitive.exclude_periods module
---

# pyacs.gts.lib.primitive.exclude_periods module


### pyacs.gts.lib.primitive.exclude_periods.exclude_periods(self, lperiod, in_place=False, verbose=False)
exclude periods of a Gts


* **Parameters**

    
    * **lperiod** – a list [start_date,end_date] or a list of periods e.g. periods=[[2000.1,2003.5],[2009.3,2010.8]]


    * **in_place** – if True, will make change in place, if False, return s a new time series



* **Note 1**

    X0,Y0,Z0 attributes will be changed if necessary



* **Note 2**

    handles both .data and .data_xyz
