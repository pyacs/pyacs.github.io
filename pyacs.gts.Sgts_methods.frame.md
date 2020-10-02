---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.Sgts_methods.frame
images: {}
path: /pyacs-gts-sgts-methods-frame
title: pyacs.gts.Sgts_methods.frame module
---

# pyacs.gts.Sgts_methods.frame module


### pyacs.gts.Sgts_methods.frame.frame(self, frame=None, euler=None, w=None, verbose=False)
Rotates the time series according to an Euler pole.
User must provide either frame, euler or w.


* **Parameters**

    
    * **frame** – str, implemented values are ‘soam’,’nas’,’nazca’,’inca’,’nas_wrt_soam’,’inca_wrt_soam’.


    * **euler** – Euler values provided either as a     string ‘euler_lon/euler_lat/euler_w’, a list [euler_lon,euler_lat,euler_w] or     a 1D numpy array np.array([euler_lon,euler_lat,euler_w])


    * **w** – rotation rate vector in rad/yr, provided either as a     string ‘wx/wy/wz’, a list [wx,wy,wz] or     a 1D numpy array np.array([wx,wy,wz])



* **Returns**

    the new Sgts instance in new frame



* **Ref**

    All values for frames are from Nocquet et al., Nat Geosc., 2014.
