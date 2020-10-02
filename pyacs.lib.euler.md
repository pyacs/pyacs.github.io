---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.euler
images: {}
path: /pyacs-lib-euler
title: pyacs.lib.euler module
---

# pyacs.lib.euler module

Euler poles manipulation


### pyacs.lib.euler.rot2euler(Wx, Wy, Wz)
Converts a rotation rate vector Wx Wy Wz in radians/yr into 
an Euler pole (long. lat. deg/Myr) into geographical (spherical) coordinates and angular velocity


* **Parameters**

    **Wx****,****Wy****,****Wz** – rotation rate vector in geocentric cartesian coordinates with units of radians/yr



* **Returns longitude,latitude,omega**

    longitude and latitude of the Euler pole in radians and the


angular velocity in decimal degrees per Myr.


* **Note**

    longitude and latitude are relative to the sphere, not the ellipsoid. This is because


Euler pole and rigid rotations only have sense on a sphere.


### pyacs.lib.euler.euler2rot(lon, lat, omega)
Converts Euler poles (long., lat., deg/Myr) into cartesian geocentric 

    rotation rate vector Wx Wy Wz in radians/yr


* **Parameters longitude,latitude,omega**

    longitude and latitude of the Euler pole in decimal degrees and the


angular velocity in decimal degrees per Myr.
:returns Wx Wy Wz: in radians/yr


* **Note**

    longitude and latitude are relative to the sphere, not the ellipsoid.



### pyacs.lib.euler.euler_uncertainty(w, vcv)
Calculates Euler pole parameters uncertainty


* **Parameters**

    
    * **w** – rotation vector in XYZ coordinates as numpy 1D array


    * **vcv** – covariance of w as numpy 2D array



* **Returns**

    vcv_euler as numpy 2D array



### pyacs.lib.euler.vel_from_euler(lonp, latp, lon_euler, lat_euler, omega_euler)
Return the horizontal velocity predicted at lonp,latp from an Euler pole


* **Parameters**

    
    * **lonp****,****latp** – longitude,latitude in decimal degrees where velocity will be predicted


    * **lon_euler****,****lat_euler_omega_euler** – longitude and latitude of the Euler pole in decimal degrees and the


angular velocity in decimal degrees per Myr.


* **Returns**

    ve,vn in mm/yr



### pyacs.lib.euler.pole_matrix(coor)
Calculates the matrix relating the horizontal velocity to a rotation rate vector.
Given a 2D-numpy array of n positions [lonp , latp] in decimal degrees the return matrix is W so that
np.dot( W , w ) gives a 2D-numpy array of [ve1,vn1,ve2,vn2,….] expressed in m/yr for a rotation rate vector in rad/yr


* **Parameters**

    **coor** – 2D numpy array of [lon, lat] in decimal degrees



* **Returns**

    the pole matrix as a 2D-numpy array



### pyacs.lib.euler.pole_matrix_fault(coor, strike, order=None)
Calculates the matrix relating the along strike and normal slip components of a fault to a rotation rate vector.
Given a 2D-numpy array of n positions [lonp , latp] in decimal degrees and strike counter-clockwise from north the return matrix is W so that
np.dot( W , w ) gives a 2D-numpy array of [ss1,ns1,ss2,ns2,….] expressed in m/yr for a rotation rate vector in rad/yr

:param coor  : 2D numpy array of [lon, lat] in decimal degrees
:param strike: 1D numpy array of [strike] in decimal degrees


* **Returns**

    the pole matrix as a 2D-numpy array



* **Note**

    np.dot( W , w ).reshape(-1,2) gives the along strike,and normal components in two columns



* **Note**

    the value are given for the hanging-wall block (right-polygon)
