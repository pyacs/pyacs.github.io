---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.Sgts
images: {}
path: /pyacs-gts-sgts
title: pyacs.gts.Sgts module
---

# pyacs.gts.Sgts module

Super Class of Geodetic Time Series Class & methods (Sgts)
Sgts is a record of Gts and enables to apply methods at the same time to various Gts


### class pyacs.gts.Sgts.Sgts(ts_dir='.', add_key='', verbose=True, name_filter='', read=True, sites=[], lexclude=[], type=None, xyz=True)
Bases: `object`


#### append(gts)
Append a Gts to the current Sgts


* **Parameters**

    **gts** – Gts instance to be appended to the current Sgts instance



#### common_mode(lref=[], detrend_method='detrend_median', method='median', verbose=True)
calculates a common mode


* **Parameters**

    
    * **lref** – liste of site codes used to calculate the common mode


    * **detrend_method** – ‘detrend_median’ or ‘detrend’, method used to detrend the reference sites time series


    * **method** – method to calculate the common mode ‘median’ or ‘mean’



* **Returns**

    a Sgts instance with filtered time series. This new instance has a _CMM time series for the common mode



* **Note**

    time series are assumed to be daily time series



#### copy()
makes a (deep) copy of the Sgts object

:return : a new Sgts instance


#### delts(code)
Delete a time series from an Sgts instance


* **Parameters**

    **code** – code to be excluded



#### frame(frame=None, euler=None, w=None, verbose=False)
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



#### gts(method, \*args, \*\*kwargs)
apply a gts method to all Gts instance of the current Sgts object


* **Parameters**

    
    * **method** – Gts method to be applied as string


    * **\*arg** – arguments for the Gts method to be applied



    * **\*\*kwarg** – keyword arguments for the Gts method to be applied



:example : ts.gts(‘detrend’,periods=[2010.0,2013.0])


#### has_ts(code)
Tests whether a time series exists in the current Sgts instance


* **Parameters**

    **code** – 4-character code



#### lGts(lexclude=[], linclude=[])
Returns the list of Gts in the current Sgts
:param lexclude: list of sites to be excluded
:param linclude: list of sites to be included, excluding all other.


#### lcode(lexclude=[], linclude=[])
Returns the list of Gts codes in the current Sgts
exclude is a list of code to be excluded


* **Parameters**

    
    * **lexclude** – list of sites to be excluded


    * **linclude** – list of sites to be included, excluding all other.



#### medvel(outdir=None, verbose=False)
Automatic velocity estimates using median estimator.
The code is adapted from the MIDAS approach (Blewitt et al., 2016).

medvel fills the velocity attribute of every Gts from the current Sgts instance.

returns the modified Sgts instance
Optionally, if outdir option is provided, writes the results in outdir


* **Param**

    outdir: output directory, default None



* **Param**

    verbose: boolean, verbose mode



* **Param**

    warning: output warning file



* **Reference**

    Blewitt, G., Kreemer, C., Hammond, W. C., & Gazeaux, J. (2016). MIDAS robust trend estimator for accurate GPS station velocities without step detection. Journal of Geophysical Research: Solid Earth, 121(3), 2054-2068.



#### n(lexclude=[], linclude=[])
Returns the number of Gts codes in the current Sgts
exclude is a list of code to be excluded


* **Parameters**

    
    * **lexclude** – list of sites to be excluded


    * **linclude** – list of sites to be included, excluding all other.



#### read_gmt(gmt=True, verbose=False, vel=False)
Reads a gmt psvelo file and populates lon and lat attributes for each Gts of Sgts


* **Parameters**

    
    * **gmt** – if True tries to read ‘/../stat/pyacs_void.gmt’, if a string then it is the gmt file to be read.


    * **verbose** – verbose mode


    * **vel** – boolean. If True, fills the .velocity attribute of every time series with the values read in the gmt file.



* **Note**

    this method is always in place.



#### read_gts_conf(gts_conf_file, verbose=False)
Reads a gts_conf_file
implemented commands in the file are:
#todo add_break      [site]  [date] # date is either [decyear] [doy year] [mday month year]
apply_offset   [site]  [offset_north,offset_east,offset_up] [date] # offset  applied is in mm, date is either [decyear] [doy year] [mday month year]
remove_offset   [site]  [offset_north,offset_east,offset_up] [date] # offset removed is in mm, date is either [decyear] [doy year] [mday month year]
#todo extract_periods [site] [date1,date2] # date is either [decyear] [doy year] [mday month year]
#todo exclude_periods [site] [date1,date2] # date is either [decyear] [doy year] [mday month year]
#todo remove_day    [site] [date]


#### read_soln(soln, verbose=True)
read a IGS soln file and add an offsets_dates for any P change in soln.


* **Parameters**

    **soln** – soln.snx IGS file



* **Note**

    the method is in place



#### read_ts(ts_dir='.', verbose=True, name_filter='', add_key='', sites=[], lexclude=[], type=None, xyz=True)
Reads time series, trying to guess the format. Current time series format supported are: pos, kenv, mb_file, cats, txyz (pyacs), track (NEU format for high rate)


* **Parameters**

    
    * **ts_dir** – directory of time series files


    * **name_filter** – string used to filter time series name ‘*name_filter*’


    * **add_key** – adds a string before site code


    * **sites** – list of site codes to be read. Any other will be discarded.


    * **lexclude** – list of sites to be excluded from reading


    * **type** – specifies the format of the time series files. Choose among [‘pos’, ‘kenv’, ‘mb_file’, ‘cats’, ‘txyz’, ‘track’ , ‘pride’,’pck’]


    * **xyz** – for pos files, reads the XYZ coordinates rather than dNEU. This is the default.



* **Returns**

    an Sgts instance.



#### same_site(dc=10, in_place=True, verbose=False)
Check that all gts in the current Sgts are actually the same site. If a given time series is
found to be of two separate sites, then a new gts is added to the return Sgts instance.

param dc: critical distance to decide to split the time series
param in_place: if True modify current Sgts, False retuen a new Sgts
param verbose: verbose mode

return: a new Sgts instance


#### save_velocity(vel_file='../stat/vel')
save horizontal and up velocities


#### sel_period(period, min_data=2, verbose=True)
selects time series having some data for a given period


* **Parameters**

    
    * **period** – [start,end], start and end period as decimal years


    * **min_data** – minimum number of data for a time series to be kept



* **Pram verbose**

    verbose mode



* **Returns**

    a new Sgts instance



#### sel_rectangle(bounds, verbose=True)
selects the time series for sites within a rectangles


* **Parameters**

    **bounds** – [lon_min,lon_max,lat_min,lat_max]



* **Pram verbose**

    verbose mode



* **Returns**

    a new Sgts instance



#### show_map(bounds=None, highlight=[])
Show a simple map of site location


#### stat_site(lsite=[], lsite_file=None, verbose=False, save_dir=None)
basic statistics about individual time series


* **Parameters**

    
    * **lsite** – list of selected sites for statistics


    * **lsite_file** – list of selected sites for statistics provided as a file


    * **verbose** – verbose mode


    * **save_dir** – directory where statistics files will be written



#### sub(lexclude=[], linclude=[])
Returns a new Sgts instance excluding Gts with code in lexclude and keeping Gts with code in include


* **Parameters**

    
    * **lexclude** – list of sites to be excluded


    * **linclude** – list of sites to be included, excluding all other.



#### to_displacement(verbose=True, base_name='vel', wdir='.', up=False)
print displacements every dates as gmt psvelo files


#### write_pck(outfile, verbose=True)
writes a Sgts object as a pck (pickle)


* **Parameters**

    
    * **outfile** – output file name. If not provided, a pck extension will be added.


    * **verbose** – verbose mode
