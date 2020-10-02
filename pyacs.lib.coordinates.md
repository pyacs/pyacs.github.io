---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.coordinates
images: {}
path: /pyacs-lib-coordinates
title: pyacs.lib.coordinates module
---

# pyacs.lib.coordinates module

Coordinates library.

– Local/Geocentric frame conversion

– Geodetic/Geocentric frame conversion

– Spherical/Geocentric conversion

– Geodetic/Flat Earth conversion


### pyacs.lib.coordinates.mat_rot_general_to_local(lam, phi, unit='radians')
Generates the conversion matrix R from general geocentric cartesian coordinates (XYZ) to local cartesian coordinates (ENU):


* **Parameters**

    
    * **lam****,****phi** – longitude


    * **unit** – ‘radians’ or ‘dec_deg’ (default is ‘radians’)



* **Returns**

    R as a 2D numpy array



* **Note**

    R = [[-sin(lambda)            cos(lambda)         0       ],


[-sin(phi)\*cos(lambda) , -sin(phi)\*sin(lamda) , cos(phi)],

[ cos(phi)\*cos(lambda) , cos(phi)\*sin(lamda) , sin(phi)]]


### pyacs.lib.coordinates.mat_rot_local_to_general(lam, phi, unit='radians')
Generates the conversion matrix R from local cartesian coordinates (ENU) to general geocentric cartesian coordinates (XYZ):


* **Parameters**

    
    * **lam****,****phi** – longitude in radians


    * **unit** – ‘radians’ or ‘dec_deg’ (default is ‘radians’)



* **Returns**

    R as a 2D numpy array



* **Note**

    Since R is orthogonal, it is the inverse and also the transpose of the conversion matrix from general geocentric cartesian coordinates (XYZ) to local cartesian coordinates (ENU)



### pyacs.lib.coordinates.denu_at_x0y0z0_to_xyz(de, dn, du, x0, y0, z0)
Converts a local vector [dn,de,du] at [x0,y0,z0] in geocentric cartesian coordinates
into X,Y,Z geocentric cartesian coordinates


* **Parameters**

    
    * **de****,****dn****,****du** – east,north, up components of the local vector in meters


    * **x0****,****x0****,****z0** – reference point for the local vector in geocentric cartesian coordinates



* **Returns**

    x,y,z in geocentric cartesian coordinates



### pyacs.lib.coordinates.xyz2geo(x, y, z, A=6378137.0, E2=0.006694380022903, unit='radians')
Converts geocentric cartesian coordinates (XYZ) to geodetic coordinates (lambda,phi,h)


* **Parameters**

    
    * **x****,****y****,****z** – XYZ coordinates in meters


    * **unit** – ‘radians’ or ‘dec_deg’ (default is ‘radians’)



* **Returns**

    long,lat,he: longitude and latitude in radians, he in meters above the ellipsoid



* **Note**

    Default ellipsoid is GRS80 used for WGS84 with


A  = 6378137.         # semi major axis = equatorial radius

E2 = 0.00669438003    # eccentricity and then

F = 1.0 - sqrt(1-E2)  # flattening


* **Ref**

    Bowring, 1985, The accuracy of geodetic latitude and height equations, Survey Review, 28, 202-206.



### pyacs.lib.coordinates.geo2xyz(llambda, phi, he, unit='radians', A=6378137.0, E2=0.006694380022903)
Converts geodetic coordinates (long,lat,he) to geocentric cartesian coordinates (XYZ)


* **Parameters**

    
    * **llambda****,****phi** – longitude, latitude


    * **he** – ellipsoidal height in meters


    * **unit** – ‘radians’ or ‘dec_deg’ for llambda and phi (default is ‘radians’)



* **Returns**

    x,y,z in meters



* **Note**

    Default ellipsoid is GRS80 used for WGS84 with


A  = 6378137.         # semi major axis = equatorial radius

E2 = 0.00669438003    # eccentricity and then

F = 1.0 - sqrt(1-E2)  # flattening


### pyacs.lib.coordinates.wnorm(phi, A=6378137.0, E2=0.006694380022903)
Calculates the geodetic radius normal to the ellipsoid


### pyacs.lib.coordinates.xyz2geospheric(x, y, z, unit='radians')
Converts geocentric cartesian coordinates (XYZ) to geo-spherical coordinates (longitude,latitude,radius).


* **Parameters**

    
    * **x****,****y****,****z** – geocentric cartesian coordinates in meters


    * **unit** – ‘radians’ or ‘dec_deg’ (default is ‘radians’)



* **Returns**

    longitude,latitude (in radians), radius from the Earth’s center in meters



* **Note**

    Be aware that the obtained coordinates are not what is usually taken as spherical coordinates, which uses co-latitude



### pyacs.lib.coordinates.xyz_spherical_distance(x1, y1, z1, x2, y2, z2, Rt=6371000.0)
Returns the spherical distance between two points of XYZ coordinates x1,y1,z1 and x2,y2,z2


* **Parameters**

    
    * **x1****,****y1****,****z1****,****x2****,****y2****,****z2** – in meters


    * **Rt** – mean Earth’s radius in meters (default 6 371 000.0 m)



* **Returns**

    distance in meters



### pyacs.lib.coordinates.geo_spherical_distance(lon1, lat1, h1, lon2, lat2, h2, unit='radians', Rt=6371000.0)
Returns the spherical distance between two points of geodetic coordinates lon1,lat1,lon2,lat2


* **Parameters**

    
    * **lon1****,****lat1****,****h1****,****lon2****,****lat2****,****h2** – longitude, latitude, radius


    * **unit** – ‘radians’ or ‘dec_deg’ for lon & lat (default is ‘radians’)


    * **Rt** – mean Earth’s radius in meters (default 6 371 000.0 m)



* **Returns**

    distance in meters



### pyacs.lib.coordinates.azimuth_to_en(azimuth)
converts an azimuth (clockwise from north) to east and north unit vector


* **Parameters**

    **azimuth** – azimuth in decimal degrees



* **Return east,north**

    unit vector



* **Note**

    calculation is made using the sphere



### pyacs.lib.coordinates.geo2flat_earth(longitude, latitude)
Converts geographical coordinates to flat earth approximation
using GMT project -N -Q -Fpq command


* **Parameters**

    **longitude****,****latitude** – geographical (ellipsoid) coordinates in decimal degrees. Also works with 1D numpy arrays



* **Returns x,y**

    in km



### pyacs.lib.coordinates.spherical_baseline_length_rate(slon, slat, sve, svn, elon, elat, eve, evn, sigma=None, verbose=False)
calculates the baseline (great circle) length rate of change between two points


* **Parameters**

    
    * **slon****,****slat** – coordinates of profile start point (decimal degrees)


    * **sve****,****svn** – east and north components of start point (mm/yr)


    * **elon****,****elat** – coordinates of profile end   point (decimal degrees)


    * **eve****,****evn** – east and north components of end point (mm/yr)


    * **sigma** – list of velocities uncertainties: [sig_sve, sig_svn, corr_sven, sig_eve, sig_evn, corr_even]


:return         :  length, rate, 1D strain rate
