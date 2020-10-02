---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.extract_dates
images: {}
path: /pyacs-gts-lib-primitive-extract-dates
title: pyacs.gts.lib.primitive.extract_dates module
---

# pyacs.gts.lib.primitive.extract_dates module


### pyacs.gts.lib.primitive.extract_dates.extract_dates(self, dates, tol=0.05, in_place=False, verbose=True)
Returns a time series extracted for a given list of dates


* **Parameters**

    
    * **dates** – dates either as a list or  1D numpy array of decimal dates


    * **tol** – date tolerance in days to assert that two dates are equal (default 0.05 day)


    * **in_place** – if True, will make change in place, if False, return s a new time series


    * **verbose** – boolean, verbose mode
