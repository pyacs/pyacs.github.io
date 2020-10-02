---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.add_obs
images: {}
path: /pyacs-gts-lib-primitive-add-obs
title: pyacs.gts.lib.primitive.add_obs module
---

# pyacs.gts.lib.primitive.add_obs module


### pyacs.gts.lib.primitive.add_obs.add_obs(self, date, NEUSNSESUCNECNUCEU, in_place=False, check=True, verbose=False)
Adds observation(s) as DN,DE,DU to a time series


* **Parameters**

    
    * **date** – date in decimal year. float, a list or 1D numpy array


    * **NEUSNSESUCNECNUCEU** – value to be added in the Gts, provided as a list, a 1D numpy array or a 2D numpy array.
    requires at least NEU: North, East, UP values
    optional: SN, SE, SU, CNE, CNU, CEU: standard deviations and correlation coefficient between North, East and Up components.
    If not provided, SN=SE=SU=0.001 (1 mm) and CNE=CNU=CEU=0


    * **in_place** – boolean, if True add_obs to the current Gts, if False, returns a new Gts


    * **check** – check time order and duplicate dates


    * **verbose** – verbose mode


:return : new Gts or the modified Gts if in_place
:note : if it exists, .data_xyz will be set to None for consistency.
