---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.gmtpoint
images: {}
path: /pyacs-lib-gmtpoint
title: pyacs.lib.gmtpoint module
---

# pyacs.lib.gmtpoint module


### class pyacs.lib.gmtpoint.GMT_Point(code=None, lon=None, lat=None, he=0, Ve=None, Vn=None, Vu=0, SVe=0, SVn=0, SVu=0, SVen=0, Cv_xyz=None, Cv_enu=None, index=None)
Bases: `object`

Simple Point Class

Attributes (mandatory)
lon: longitude (decimal degrees)
lat: latitude (decimal degrees)

Attributes (optinal):
code : 4-letters code
he : height above the ellipsoid
ve, vn: east & north components of velocity 
sve,svn,sven: formal error (standard deviation) on velocity component and correlation [-1,1]


#### copy()

#### get_info(display=False, legend=False, verbose=False)
Print information of the current GMT_Point


#### magaz()
Returns norm & azimuth of velocity from the current GMT_Point


* **Returns**

    norm,azimuth in mm/yr and decimal degree clockwise from North



* **Note**

    sigmas not implemented yet



#### assign_index(index)
Assigns an index to the current GMT_Point.
Useful for building linear systems.


* **Parameters**

    **index** – index


:return : the modified GMT_Point instance


#### get_index()
Returns index of the current GMT_Point


* **Returns**

    index



#### spherical_distance(M)
Returns spherical distance between two GMT_Point (in meters)


* **Parameters**

    **M** – GMT_Point instance


:return : distance along the sphere between current instance and M


#### pole(W=None, SW=None, type_euler='rot', option='predict')
Substract the prediction of a given Euler pole


#### add_to_gmt_psvelo(fname, overwrite=False, verbose=False)
Adds the current GMT_Point to a gmt psvelo file


* **Parameters**

    
    * **fname** – gmt psvelo file


    * **overwrite** – will overwrite the line corresponding having the same code (default is False), generate an error otherwises


    * **verbose** – verbose mode



#### rotate_vel(angle, unit='radians')
Rotate a vector of angle (clockwise)


* **Parameters**

    
    * **angle** – angle


    * **unit** – ‘dec_deg’ or ‘radians’ (default radians)


:return : rotated components of velocity


#### midpoint(point, code='Mm')
returns the mid-point between two GMT_Point


* **Parameters**

    **point** – GMT_Point


:return : mid_point as GMT_Point
