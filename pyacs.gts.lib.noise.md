---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.noise
images: {}
path: /pyacs-gts-lib-noise
title: pyacs.gts.lib.noise module
---

# pyacs.gts.lib.noise module

Pyacs noise module
This is a wrapper to Globk tsfit and the CATS Software
Reference
Herring, T. A., King, R. W., Floyd, M. A. & McClusky, S. C. (2015). GAMIT/GLOBK Reference manual, 10.6. 
Williams, S. D. (2008). CATS: GPS coordinate time series analysis software. GPS solutions, 12(2), 147-153.


### pyacs.gts.lib.noise.wrms(self)
Return the wrms


* **Return wrms**

    return(np.array([wrms_n,wrms_e,wrms_up]))



### pyacs.gts.lib.noise.realistic_sigma(self, option='tsfit', in_place=False, verbose=False)
Calculates realistic sigmas on velocity components
:param option:

> 
> * tsfit: globk T. Herring realistic sigma


> * cats_pl: CATS estimates with noise type estimated (i.e. –model=pl:)


> * cats_seasonal_pl: CATS estimates with seasonal terms and noise type estimated (i.e. –model=pl: –sinusoid=1y1)


> * cats_flicker: CATS estimates assuming flicker noise (i.e. –model=pl:k-1)


> * cats_seasonal_flicker: CATS estimates with seasonal terms and assuming flicker noise (i.e. –model=pl:k-1 –sinusoid=1y1)


### pyacs.gts.lib.noise.sigma_cats(self, in_place=False, verbose=False, k='k-1', seasonal='')
runs CATS for getting realistic sigma


### pyacs.gts.lib.noise.sigma_vel_tsfit(self, in_place=False, verbose=False)
runs tsfit for getting realistic sigma


### pyacs.gts.lib.noise.get_spectral_index(cats_file)

### pyacs.gts.lib.noise.get_vel_and_sigma(cats_file)
