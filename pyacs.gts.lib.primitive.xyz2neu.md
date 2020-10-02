---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.xyz2neu
images: {}
path: /pyacs-gts-lib-primitive-xyz-2-neu
title: pyacs.gts.lib.primitive.xyz2neu module
---

# pyacs.gts.lib.primitive.xyz2neu module


### pyacs.gts.lib.primitive.xyz2neu.xyz2neu(self, corr=False, ref_xyz=None, verbose=False)
populates neu (data) using xyz (data_xyz)
lon, lat and h will also be set.


* **Parameters**

    
    * **corr** – if True, then standard deviation and correlations will also be calculated


    * **ref_xyz** – [X,Y,Z] corresponding to the 0 of the local NEU frame. If not provided, the first position is used as a reference


    * **verbose** – verbose mode



* **Note**

    this method is always in place
