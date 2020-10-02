---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.tsr
images: {}
path: /pyacs-gts-tsr
title: pyacs.gts.tsr module
---

# pyacs.gts.tsr module

Time series express as a 4D-numpy array D and a separate observation time vector T

> D(i,j,k) would be the displacement
> observation time index i
> for site j
> for component k [0,1,2,3,4,5] [de,dn,du,sde,sdn,sdu]

> no data are NaN


### class pyacs.gts.tsr.tsr()
Bases: `object`


#### classmethod convert(sgts, tol=0.01, verbose=False)
Convert an Sgts object into a tsr


* **Parameters**

    **sgts** – Sgts object


:param tol : tolerance in decimal day to assign the same date
