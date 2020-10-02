---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.vel_field
images: {}
path: /pyacs-lib-vel-field
title: pyacs.lib.vel_field module
---

# pyacs.lib.vel_field module


### class pyacs.lib.vel_field.Velocity_Field(file_name=None, name=None, lgmt_points=None, verbose=False)
Bases: `object`

Velocity_Field class: reads a velocity field from a GMT psvelo file 
and provides methods to manipulate velocity field


#### classmethod read(file_name=None, lexclude=[], lonly=[], verbose=False)
Reads a GMT psvelo file


#### info(details=True)
Print basics information


#### add_point(M)
Appends a GMT_Point to a velocity field


#### remove_point(code)
Removes the a GMT_Point to a velocity field given its code


* **Parameters**

    **code** – 4-characters code for the point to be removed



#### write(out_file=None, lexclude=[], verbose=True, comment='', up=False)
Writes a GMT psvelo file
a list site name to be excluded can be provided


#### nsites()
Returns the number of sites in velocity field


#### l_GMT_Point()
Returns the velocity field as a list of GMT_Point object


#### print_info_site(code, verbose=False)
Print the info for a given site by his code


#### subset(lonly=None, lexclude=None)
Returns a new Velocity_Field object from a subset of sites


* **Parameters**

    **lonly****,****lexclude** – list of site codes to be included or excluded



#### radial(center)
Returns a Velocity Field whose components are radial and tangential with respect to a given center


* **Parameters**

    **center** – numpy array [longitude,latitude] of center



#### lcode()
Returns a list of all point codes in current Velocity Field object


#### site(code)
Returns a site in current Field object as a GMT_Point object


#### calc_pole(plates, method='WLS', verbose=False)
Performs Euler pole calculation


* **Parameters**

    
    * **plates** – dictionary with the name of plate as key and list of sites for each plate as values


    * **method** – choose among weighted least-squares ‘WLS’ or ‘L1’



* **Output**

    for each plate, the following files will be created:
    - euler_stat_plate_name.dat: Euler pole values and statistics
    - plate_name.gmt: velocities (GMT psvelo format) with respect to the calculated Euler pole
    - plate_name.shp: velocities (shapefile  format) with respect to the calculated Euler pole
    - eulers_sum.dat: summary of Euler pole values



#### pole(lexclude=[], method='WLS', exp='pLate', log=None)
Euler pole calculation; available optimization methods are WLS: weighted least squares, LS: least-squares, Dikin: L1 linear estimator


#### substract_pole(W=None, type_euler='rot')
substract the prediction of an Euler pole to the velocity field


#### common(linGpoint, prefit=10.0, lexclude=[])
Returns a list of sites common to the current Velocity Field object and the list of GMT_Points provided in argument
Coordinates will be the ones from the Sinex and NOT from the list of Gpoints
Commons point are points with same code pt and soln


#### proj_profile(slon, slat, elon, elat, d, save=None, verbose=False)
project velocity components along a great circle defined by initial/stop points (slon,slat,elon,elat)


* **Parameters**

    
    * **slon****,****slat** – coordinates of profile start point (decimal degrees)


    * **elon****,****elat** – coordinates of profile end   point (decimal degrees)


:param d        : maximum distance for a point to be considered
:param save     : output file name (optional)

:return         :  numpy 1D array with
np_code, np_distance_along_profile, np_distance_to_profile ,                 np_Ve , np_Vn , np_SVe , np_SVn ,                 np_v_parallele , np_v_perpendicular ,                 np_sigma_v_parallele , np_sigma_v_perpendicular , np_lazimuth


#### strain(lcode, save=None, method='WLS', verbose=False)
Calculates the strain rate given a list of sites


* **Parameters**

    **lcode** – list of site names


:param save  : file to save the result
:param method: estimator in ‘L1’,’WLS’ (default: weighted least-squares ‘WLS’)
:param verbose: verbose mode
