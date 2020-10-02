---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.set_zero_at_date
images: {}
path: /pyacs-gts-lib-primitive-set-zero-at-date
title: pyacs.gts.lib.primitive.set_zero_at_date module
---

# pyacs.gts.lib.primitive.set_zero_at_date module


### pyacs.gts.lib.primitive.set_zero_at_date.set_zero_at_date(self, date, offset=None, in_place=False)
make a translation of a time series, setting to 0 at a given date
if the provided date does not exist, uses the next date available


* **Parameters**

    
    * **date** – date in decimal year


    * **offset** – an offset (in mm) to be added. Could be a float, a list or 1D numpy array with 3 elements
