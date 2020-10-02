---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.extract_ndates_after_date
images: {}
path: /pyacs-gts-lib-primitive-extract-ndates-after-date
title: pyacs.gts.lib.primitive.extract_ndates_after_date module
---

# pyacs.gts.lib.primitive.extract_ndates_after_date module


### pyacs.gts.lib.primitive.extract_ndates_after_date.extract_ndates_after_date(self, date, n, verbose=False)
Extract n values after a given date
If n values are not available, returns all available values after date
.data is set to None if no value at all is available


* **Parameters**

    
    * **date** – date in decimal year


    * **n** – number of observations to be extracted



* **Returns**

    a new Gts
