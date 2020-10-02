---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.metadata
images: {}
path: /pyacs-gts-lib-metadata
title: pyacs.gts.lib.metadata module
---

# pyacs.gts.lib.metadata module


### pyacs.gts.lib.metadata.read_lon_lat(self, gmt_file, verbose=False)
Reads a gmt psvelo file and populates Gts.lon & Gts.lat


* **Parameters**

    
    * **gmt_file** – gmt psvelo file


    * **verbose** – verbose mode (boolean)



* **Returns**

    the current Gts instance



### pyacs.gts.lib.metadata.save_velocity(self, gmt_file, verbose=True, comment=None, up=False)
Appends velocity estimates (with uncertainties) to a gmt psvelo file


* **Parameters**

    
    * **gmt_file** – output gmt psvelo file (will append if gmt_file already exists)


    * **verbose** – verbose mode (boolean)


    * **comment** – comment as a string. ‘# ‘ is pre-prended to comment if not provided


    * **up** – boolean. If True, then Ve, SVe and SVen are set to 0 and Vu and Vu are written as 4-th and 6-th fields



* **Returns**

    the current Gts instance



### pyacs.gts.lib.metadata.save_offsets(self, ofile, verbose=True, comment='', up=False, info=False)
Appends offsets values to a given text file (gmt psvelo format)


* **Parameters**

    
    * **ofile** – output offset file


    * **verbose** – verbose mode (boolean)


    * **comment** – comment as a string. ‘# ‘ is pre-prended to comment if not provided


    * **up** – boolean. If True, then Ve, SVe and SVen are set to 0 and Vu and Vu are written as 4-th and 6-th fields



* **Returns**

    the current Gts instance



### pyacs.gts.lib.metadata.read_eq_rename(self, eq_rename, in_place=False, verbose=False)
Reads the information for the current site (code) from an eq_rename globk file.

Populates loutliers and offsets_dates
Found excluded periods in the eq_rename file are added to loutliers


* **Parameters**

    
    * **eq_rename** – eq_rename (globk format) file to be read


    * **in_place** – boolean. If True then the Gts instance is modified, if False the Gts instance is preserved and a new Gts instance is return


    * **verbose** – verbose mode (boolean)



* **Returns**

    Gts instance



### pyacs.gts.lib.metadata.save_eq_rename(self, eq_rename, verbose=False, excluded_periods=None)
save results of a Gts analysis in globk format eq_rename


* **Parameters**

    
    * **eq_rename** – output eq_rename file (Golbk format)


    * **verbose** – verbose mode (boolean)


    * **exluded_periods** – periods to be excluded



* **Returns**

    Gts instance



### pyacs.gts.lib.metadata.make_dynamic_apr(self, apr, time_step=30.0, pos_tol=0.03, dates=[], gap=20.0, verbose=False)
Creates an apr file for GAMIT
The created apr file has no velocity, but a series of coordinates at different time


* **Parameters**

    
    * **apr** – apr file (Globk format)


    * **time_step** – time step for writing dates (default 30 days)


    * **pos_tol** – position tolerance. If exceeded, a new date will be written. (default 0.03 m)


    * **dates** – a list of dates in decimal years where writing will be forced


    * **gap** – gap in days. If there is no data during a duration greater than gap, then observation is forced to be included and tested against pos_tol


    * **verbose** – verbose mode (boolean)



* **Returns**

    Gts instance



### pyacs.gts.lib.metadata.save_apr(self, apr, epoch=None, verbose=False, excluded_periods=None)
save results of a Gts analysis in globk format apr file


* **Parameters**

    
    * **apr** – apr file (Globk format)


    * **epoch** – epoch in decimal year for coordinates in apr


    * **verbose** – verbose mode (boolean)


    * **exluded_periods** – periods to be excluded



* **Returns**

    Gts instance



* **Note**

    following Globk’s convention, site will be named XXXX_1PS, XXXX_2PS etc between offset dates



### pyacs.gts.lib.metadata.read_offset_dates(self, offset_file)
Reads an offset file and populates offsets_dates (pyacs format) attribute of the current Gts instance.
format is simply a code dates. dates can be any format read by pyacs.guess_date


* **Parameters**

    **offset_file** – offset_file to be read



* **Returns**

    the current Gts instance



### pyacs.gts.lib.metadata.info(self, info=2)
Print various informations about the time series
