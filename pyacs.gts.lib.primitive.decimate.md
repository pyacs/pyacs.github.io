---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.decimate
images: {}
path: /pyacs-gts-lib-primitive-decimate
title: pyacs.gts.lib.primitive.decimate module
---

# pyacs.gts.lib.primitive.decimate module


### pyacs.gts.lib.primitive.decimate.decimate(self, time_step=30.0, dates=[], method='median', verbose=False)
decimate a time series


* **Parameters**

    
    * **time_step** – time step in days


    * **dates** – list of dates where point are forced to be written regardless time_step


    * **method** – method used to be used to calculated the position. choose among [‘median’,’mean’,’exact’]


    * **verbose** – verbose mode


:return : new Gts
