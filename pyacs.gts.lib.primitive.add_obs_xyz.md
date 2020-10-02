---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.add_obs_xyz
images: {}
path: /pyacs-gts-lib-primitive-add-obs-xyz
title: pyacs.gts.lib.primitive.add_obs_xyz module
---

# pyacs.gts.lib.primitive.add_obs_xyz module


### pyacs.gts.lib.primitive.add_obs_xyz.add_obs_xyz(self, date, XYZSXSYSZCXYCXZCYZ, in_place=False, check=True, neu=True, verbose=False)
Adds observation(s) as XYZ to a time series


* **Parameters**

    
    * **date** – date in decimal year. float, a list or 1D numpy array


    * **XYZSXSYSZCXYCXZCYZ** – value to be added in the Gts, provided as a list, a 1D numpy array or a 2D numpy array.    requires at least X,Y,Z


optional: SX, SY, SZ, CXY, CXZ, CYZ: standard deviations and correlation coefficients.    If not provided, SX=SY=SZ=0.001 (1 mm) and CXY=CXZ=CYZ=0
:param in_place: boolean, if True add_obs to the current Gts, if False, returns a new Gts
:param check: check time order , duplicate dates and re-generate NEU time series (.data)
:param neu: regenerate .data from the updated .data_xyz
:param verbose: verbose mode

:return : new Gts or the modified Gts if in_place
:note 1: by default .data will be updated from .data_xyz, and X0,Y0,Z0 will be updated.
:note 2:
