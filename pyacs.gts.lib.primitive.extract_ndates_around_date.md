---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.extract_ndates_around_date
images: {}
path: /pyacs-gts-lib-primitive-extract-ndates-around-date
title: pyacs.gts.lib.primitive.extract_ndates_around_date module
---

# pyacs.gts.lib.primitive.extract_ndates_around_date module


### pyacs.gts.lib.primitive.extract_ndates_around_date.extract_ndates_around_date(self, date, n)
Extract n values before and n values after a given date
If n values are not available, returns all available values
.data is set to None if no value at all is available


* **Parameters**

    
    * **date** – date in decimal year


    * **n** – number of observations to be extracted



* **Returns**

    a new Gts
