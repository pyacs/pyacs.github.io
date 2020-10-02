---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.tensor_ts.sgts2tsr
images: {}
path: /pyacs-gts-lib-tensor-ts-sgts-2-tsr
title: pyacs.gts.lib.tensor_ts.sgts2tsr module
---

# pyacs.gts.lib.tensor_ts.sgts2tsr module

Time series express as a 4D-numpy array D and a separate observation time vector T

> D(i,j,k) would be the displacement
> observation time index i
> for site j
> for component k [0,1,2,3,4,5] [de,dn,du,sde,sdn,sdu]

> no data are NaN


### pyacs.gts.lib.tensor_ts.sgts2tsr.sgts2tsr(sgts, tol=0.01, verbose=False)
Convert an Sgts object into a tsr


* **Parameters**

    **sgts** – Sgts object


:param tol : tolerance in decimal day to assign the same date


* **Returns**

    NAMES (1D-Numpy string array), DATES (1D-Numpy integer array of seconds), a 4D numpy array


D(i,j,k) would be the displacement
observation time index i
for site j
for component k [0,1,2,3,4,5] [de,dn,du,sde,sdn,sdu]
