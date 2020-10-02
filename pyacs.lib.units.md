---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.units
images: {}
path: /pyacs-lib-units
title: pyacs.lib.units module
---

# pyacs.lib.units module

Various routines dealing with units conversion.


### pyacs.lib.units.mas2rad(mas)
Converts milliarcseconds to radians


* **Parameters**

    **mas** – angle in millarcseconds



* **Returns**

    rad: in radians



* **Example**


```python
>>> import pyacs
>>> pyacs.mas2rad(1.)
>>> 4.84813681109536e-09
>>> pyacs.mas2rad(np.array([1.0,2.0]))
>>> array([  4.84813681e-09,   9.69627362e-09])
```


### pyacs.lib.units.rad2mas(rad)
Converts radians to milliarcseconds


* **Parameters**

    **rad** – angle in radians



* **Returns mas**

    angle in millarcseconds:



### pyacs.lib.units.radians2deg_mn_sec(rad, angle_range='-180-180')
Converts an angle from radians to deg, minutes, seconds


* **Parameters**

    
    * **rad** – angle in radians


    * **angle_range** – either ‘-180-180’ or ‘0-360’



* **Returns**

    deg, minutes, seconds



* **Return type**

    int,int,float



### pyacs.lib.units.moment_to_magnitude(moment)
Converts a moment in N.m to Mw


* **Parameters**

    **moment** – in N.m



* **Return magnitude**

    2./3.\*(math.log10(M0)-9.05)



### pyacs.lib.units.magnitude_to_moment(magnitude)
Converts a Mw magnitude to moment in N.m


* **Parameters**

    **magnitude** – Mw



* **Return moment**

    in N.m, 10^(1.5\*magnitude+9.5)
