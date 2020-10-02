---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.faultslip
images: {}
path: /pyacs-lib-faultslip
title: pyacs.lib.faultslip module
---

# pyacs.lib.faultslip module

Various routines relating fault parameters, slip and motion across faults


### pyacs.lib.faultslip.v_to_rake(ve, vn, strike, dip, style='inverse')
for a given relative horizontal velocity (ve,vn) between two blocks separated by a fault of a given strike & dip
, returns the expected rake for the eq.


* **Parameters**

    
    * **ve****,****vn** – east and north components of motion (any unit)


    * **strike****,****dip** – in decimal degrees


    * **style** – string among {‘inverse’, ‘normal’, ‘leftlateral’,’rightlateral’}



* **Returns rake**

    in decimal degrees



* **Note**

    Because only providing ve,vn is ambiguous (we don’t know whether if ve,vn is hanging wall motion wrt the footwall or the opposite)     an additional information (style) in the form of one of {‘inverse’, ‘normal’, ‘leftlateral’,’rightlateral’} must be provided.



### pyacs.lib.faultslip.v_to_n_ss(ve, vn, strike)
for a given relative horizontal velocity (ve,vn) between two blocks separated by a fault of a given strike
, returns normal and strike-slip component of motion.
The convention is that the point is in the left-domain with respect to the fault.
Shortening & right-lateral are positive, extension and left-lateral negative


* **Parameters**

    
    * **ve****,****vn** – east and north components of motion (any unit)


    * **strike** – in decimal degrees



* **Returns normal,strike-slip**

    same units as ve,vn



### pyacs.lib.faultslip.strike_dip_rake_to_dir(strike, dip, rake)
for a given (strike,dip,rake)  returns the azimuth of the horizontal motion
:param strike,dip,rake: in decimal degrees
:returns: direction: slip direction (modulo 180 degrees)


### pyacs.lib.faultslip.rake_from_euler(longitude, latitude, strike, dip, euler)
predicts rake for a given fault according to an Euler pole, position and strike of the fault


* **Parameters**

    
    * **longitude****,****latitude** – in decimal degrees


    * **strike** – fault strike from north in decimal degrees


    * **dip** – fault dip from north in decimal degrees


    * **euler** – Euler pole as a string ‘/long/lat/w/style’ (style among ‘inverse’, ‘normal’, ‘leftlateral’,’rightlateral’)



* **Return rake**

    in decimal degrees



* **Note**

    style needs to be provided to ensure the correct sense of slip.



### pyacs.lib.faultslip.slip_rake_2_ds_ss(slip, rake)
Converts a slip vector provided as slip and rake to dip slip and strike-slip components


* **Parameters**

    
    * **slip** – slip


    * **rake** – rake in degrees


:return ( slip\*np.sin( np.radians(rake) ) ,  slip\*np.cos( np.radians(rake) ))


* **Note**


ds will be positive for rake in [0,180] that is reverse motion
ss will be positive for left-lateral motion


### pyacs.lib.faultslip.ss_ns_2_ve_vn(ss, ns, strike)
Converts strike-slip and normal slip components of a fault to ve, vn


* **Parameters**

    
    * **ss** – vector of strike-slip


    * **ns** – vector of normal-slip


    * **strike** – vector of fault strike, counter-clockwise from north in degrees



* **Returns**

    ve, vn, same unit as ss and ds



* **Note**


ss is assume to be positive for left-lateral motion
ds will be positive for reverse motion


### pyacs.lib.faultslip.geo_to_strike(ilon, ilat, elon, elat)
for a given fault segment starting at ilon,lat and ending at elon, elat
, returns the strike.


* **Parameters**

    
    * **ilon****,****ilat** – geographical coordinates of fault segment start point in decimal degrees


    * **elon****,****elat** – geographical coordinates of fault segment end point in decimal degrees



* **Returns strike**

    in decimal degrees clockwise from north



* **Note**

    strike here is taken as the initial bearing. Be cautious with long segments
