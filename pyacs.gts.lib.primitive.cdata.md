---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.cdata
images: {}
path: /pyacs-gts-lib-primitive-cdata
title: pyacs.gts.lib.primitive.cdata module
---

# pyacs.gts.lib.primitive.cdata module


### pyacs.gts.lib.primitive.cdata.cdata(self, data=False, data_xyz=False, tol=0.001, verbose=False)
Check data/data_xyz attributes


* **Parameters**

    
    * **data** – boolean, if True, data attribute will be checked


    * **data_xyz** – boolean, if True, data_xyz attribute will be checked


    * **tol** – tolerance in days for two dates to be considered as the same (default 0.001 of day)


    * **verbose** – boolean, verbose mode


:return : boolean, True if everything is OK, False otherwise

:note : in future, this routine should also whether .data and .data_xyz value are consistent
