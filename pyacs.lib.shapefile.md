---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.shapefile
images: {}
path: /pyacs-lib-shapefile
title: pyacs.lib.shapefile module
---

# pyacs.lib.shapefile module

Various subroutine to convert pyacs results to shapefiles


### pyacs.lib.shapefile.static_slip_to_shapefile(static_slip_file, shp_name, dis_type='rec', verbose=False)
Converts pyacs/pyeq slip solution into a shapefile


* **Parameters**

    
    * **static_slip_file** – output from pyeq_static_inversion.py (

    ```
    *
    ```

    sol_slip.dat)


    * **shp_name** – output shapefile name


    * **dis_type** – either ‘rec’ (rectangular dislocation) or ‘tde’ (triangular dislocation element)


    * **verbose** – verbose mode



### pyacs.lib.shapefile.psvelo_to_shapefile(psvelo_file, shp_name, verbose=False)
Converts a psvelo GMT file into shapefile


* **Parameters**

    
    * **psvelo** – GMT psvelofile


    * **shp_name** – output shapefile name


    * **verbose** – verbose mode



### pyacs.lib.shapefile.pyeblock_fault(pyeblock_file, shp_name, verbose=False)
Converts a pyeblock fault file into a shapefile


* **Parameters**

    
    * **pyeblock_fault** – pyeblock fault file


    * **shp_name** – output shapefile name


    * **verbose** – verbose mode
