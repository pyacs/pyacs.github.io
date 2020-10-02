---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.copy
images: {}
path: /pyacs-gts-lib-primitive-copy
title: pyacs.gts.lib.primitive.copy module
---

# pyacs.gts.lib.primitive.copy module


### pyacs.gts.lib.primitive.copy.copy(self, data=True, data_xyz=True, loutliers=True)
makes a (deep) copy of the time series.

By default, all attributes are also copied, including .data, .data_xyz, loutliers etc.

Default behaviour can be modified for the following attribute:


* **Parameters**

    
    * **data** – can be set to None or a 2D numpy array of shape (n,10)


    * **data_xyz** – can be set to None or a 2D numpy array of shape (n,10)


    * **loutliers** – False will not copy the loutliers atrribute
