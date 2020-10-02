---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.Gts
images: {}
path: /pyacs-gts-gts
title: pyacs.gts.Gts module
---

# pyacs.gts.Gts module

Geodetic Time Series Class & methods

A Geodetic time series (Gts) is a series of 3 components North,East,UP as a function of increasing dates

The Gts implemented in PYACS has the following structure:

Basic data

    
    * data:            a 2D numpy array with 7 columns including: dec.year, N, E, U, S_N, S_E, S_U


    * code:            station 4-letters code


    * lon,lat,h:       approximate longitude, latitude (geodetic, deg.dec) and ellipsoidal height (m)


    * X0,Y0,Z0         XYZ reference position in the Geocentric Frame. N,E,U are with respect to X0,Y0,Z0


    * t0               reference date in decimal year corresponding to the X0,Y0,Z0

Optional data

    
    * data_xyz:        a 2D numpy array with 7 columns including: dec.year, X, Y, Z, SX, SY, SZ, corr_XY, corr_XZ, corr_YZ


    * data_corr_neu    a 2D numpy array with 4 columns including: dec.year, corr_ne,corr_nu,corr_eu


    * data_corr_xyz    a 2D numpy array with 4 columns including: dec.year, corr_xy,corr_xz,corr_yz

Analysis results

    
    * outliers:        list of index of outliers in a time series (all components)


    * outliers_east    list of index of outliers on the East component in a time series


    * outliers_north   list of index of outliers on the North component in a time series


    * outliers_up      list of index of outliers on the Up component in a time series


    * offsets_values:  a 2D numpy array with 7 columns: dec.year N, E, U, S_N, S_E, S_U


    * offsets_dates:   a list of dates for offsets


    * velocity:        a 1D numpy array with 6 columns: vel_N, vel_E, vel_U, S_vel_N, S_vel_E, S_vel_U


    * annual:          a 1D numpy array with 6 columns: Amplitude_N, Phase_N, Amplitude_E, Phase_E, Amplitude_U, Phase_U


    * semi_annual:     a 1D numpy array with 6 columns: Amplitude_N, Phase_N, Amplitude_E, Phase_E, Amplitude_U, Phase_U

Metadata

    
    * ifile:          original input file of the time series


    * log:            log of operations


    * metadata:       any information the analyst would like to be recorded

Units Conventions

    
    * dates are in decimal year


    * coordinates are in meters


    * phases are in radians

Programming conventions

    
    * singular denotes single values, plural or name starting with l denotes lists or array


    * in_place=True in methods means that current content of the Gts will be overwritten; default is False


### pyacs.gts.Gts.get_index_from_dates(dates, data, tol=0.25)
returns the list of index in data corresponding to given dates within tolerance


* **Parameters**

    
    * **dates** – list of dates in decimal year


    * **data** – a 2D numpy array with decimal dates in the first column


    * **tol** – date tolerance to decide that two dates are equal. (default 0.25 day)


:return : list of index


### class pyacs.gts.Gts.Gts(code=None, lat=None, lon=None, h=None, X0=None, Y0=None, Z0=None, t0=None, data=None, data_xyz=None, data_corr_neu=None, data_corr_xyz=None, offsets_dates=[], offsets_values=None, outliers=[], annual=None, semi_annual=None, velocity=None, ifile=None, log=None, metadata=None)
Bases: `object`


#### classmethod read(tsfile, fmt=None, verbose=False)
Reads a time series file


#### add_obs(date, NEUSNSESUCNECNUCEU, in_place=False, check=True, verbose=False)
Adds observation(s) as DN,DE,DU to a time series


* **Parameters**

    
    * **date** – date in decimal year. float, a list or 1D numpy array


    * **NEUSNSESUCNECNUCEU** – value to be added in the Gts, provided as a list, a 1D numpy array or a 2D numpy array.
    requires at least NEU: North, East, UP values
    optional: SN, SE, SU, CNE, CNU, CEU: standard deviations and correlation coefficient between North, East and Up components.
    If not provided, SN=SE=SU=0.001 (1 mm) and CNE=CNU=CEU=0


    * **in_place** – boolean, if True add_obs to the current Gts, if False, returns a new Gts


    * **check** – check time order and duplicate dates


    * **verbose** – verbose mode


:return : new Gts or the modified Gts if in_place
:note : if it exists, .data_xyz will be set to None for consistency.


#### add_obs_xyz(date, XYZSXSYSZCXYCXZCYZ, in_place=False, check=True, neu=True, verbose=False)
Adds observation(s) as XYZ to a time series


* **Parameters**

    
    * **date** – date in decimal year. float, a list or 1D numpy array


    * **XYZSXSYSZCXYCXZCYZ** – value to be added in the Gts, provided as a list, a 1D numpy array or a 2D numpy array.    requires at least X,Y,Z


optional: SX, SY, SZ, CXY, CXZ, CYZ: standard deviations and correlation coefficients.    If not provided, SX=SY=SZ=0.001 (1 mm) and CXY=CXZ=CYZ=0
:param in_place: boolean, if True add_obs to the current Gts, if False, returns a new Gts
:param check: check time order , duplicate dates and re-generate NEU time series (.data)
:param neu: regenerate .data from the updated .data_xyz
:param verbose: verbose mode

:return : new Gts or the modified Gts if in_place
:note 1: by default .data will be updated from .data_xyz, and X0,Y0,Z0 will be updated.
:note 2:


#### add_offsets_dates(offsets_dates, in_place=False)
add_offsets_dates to a time series
if in_place = True then replace the current time series


#### add_vel_sigma(in_place=False, b_fn=4, verbose=True)
calculates realistic sigma on velocity components assuming white &  
flicker using eq (19) & (23) from Williams (J. of Geodesy, 2003)
b_fn is the value for flicker noise, taken as 4 mm/yr^1/4
model can be detrend, detrend_annual, detrend_seasonal 
if in_place = True then replace the current time series


#### apply_offsets(np_offset, opposite=False, in_place=False, verbose=False)
Applies given offsets to a times series
np_offset is a 1D np.array with lines [dates,north,east,up]
if in_place = True then replace the current time series


* **Parameters**

    
    * **np_offset** – 1D or 3D numpy array or list or list of list with column offset_dates, north, east, up, s_north, s_east, s_up


    * **opposite** – boolean, if True apply the oppsite of provided offsets


    * **in_place** – if True, will make change in place, if False, return s a new time series


    * **verbose** – boolean, verbose mode



#### cdata(data=False, data_xyz=False, tol=0.001, verbose=False)
Check data/data_xyz attributes


* **Parameters**

    
    * **data** – boolean, if True, data attribute will be checked


    * **data_xyz** – boolean, if True, data_xyz attribute will be checked


    * **tol** – tolerance in days for two dates to be considered as the same (default 0.001 of day)


    * **verbose** – boolean, verbose mode


:return : boolean, True if everything is OK, False otherwise

:note : in future, this routine should also whether .data and .data_xyz value are consistent


#### copy(data=True, data_xyz=True, loutliers=True)
makes a (deep) copy of the time series.

By default, all attributes are also copied, including .data, .data_xyz, loutliers etc.

Default behaviour can be modified for the following attribute:


* **Parameters**

    
    * **data** – can be set to None or a 2D numpy array of shape (n,10)


    * **data_xyz** – can be set to None or a 2D numpy array of shape (n,10)


    * **loutliers** – False will not copy the loutliers atrribute



#### correct_duplicated_dates(action='correct', tol=0.1, in_place=False, verbose=False)
Check or remove duplicated dates in a time series


* **Parameters**

    
    * **action** – ‘correct’ (default) or ‘check’


    * **tol** – tolerance for two dates to be considered as the same (default = 0.1 day)


    * **in_place** – boolean, if True,


    * **verbose** – verbose mode



#### decimate(time_step=30.0, dates=[], method='median', verbose=False)
decimate a time series


* **Parameters**

    
    * **time_step** – time step in days


    * **dates** – list of dates where point are forced to be written regardless time_step


    * **method** – method used to be used to calculated the position. choose among [‘median’,’mean’,’exact’]


    * **verbose** – verbose mode


:return : new Gts


#### decyear2days(ref_date='', in_place=False)
Converts the dates of a time series from decimal years to days after a reference date
ref_date is read by guess_date


#### delete_small_offsets(offsets, del_by_pricise=False)
The aim for test_offset modul. 
Estimate the offsets with clean data.
Then delete the offsets which their values are so small
input: list of time offsets
output: list of time offsets tested


#### detrend(method='L2', in_place=False, periods=[], exclude_periods=[])
detrends a time series and save velocity estimates in velocity attribute

:param periods         : periods used to estimate the velocity
:param exclude_periods : periods to be excluded for the velocity estimate
:param in_place        : if True then replace the current time series
:return                : the detrended time series
:note                  : outliers from Gts.outliers are omitted in the estimation and
offsets given Gts.offsets_dates are estimated simultaneously


#### detrend_annual(method='L2', in_place=False, periods=None, exclude_periods=None)
estimates a trend + annual terms in a time series and removes them
velocity and annual attribute are saved in Gts.velocity & Gts.annual

:param periods         : periods used for estimation
:param exclude_periods : periods to be excluded from estimation
:param in_place        : if True then replace the current time series
:return                : the detrended time series
:note                  : outliers from Gts.outliers are ommitted in the estimation and
offsets given Gts.offsets_dates are estimated simultaneously


#### detrend_median(delta_day=None, in_place=False, periods=[], exclude_periods=[], verbose=False, auto=False)
Calculates a velocity using the median of pair of displacements exactly separated by one year, inspired from MIDAS
If the time series has less than a year of data, then the time series is kept untouched.


* **Parameters**

    
    * **delta_day** – if None, it is one year, if 0 then it is the relax mode for campaign data, 
    any integer is the time delta (in days) used to compute velocity.


    * **in_place** – boolean, if True, in_place, if False, returns a new Gts instance (default)


    * **periods** – periods (list of lists) to be included for trend calculation


    * **exclude_periods** – periods (list of lists) to be excluded for trend calculation


    * **verbose** – verbose mode


    * **auto** – if True, then start will delta_day=None, if it fails or found less than 100 pairs then use delta_day=0,


if fails then use regular detrend


* **Note**

    returns None if time series is shorter than 1 year



#### detrend_seasonal(method='L2', in_place=False, periods=None, exclude_periods=None)
estimates a trend + annual + semi-annual terms in a time series and removes them
velocity, annual and semi-annual attributes are saved in Gts.velocity, Gts.annual, Gts.semi_annual

:param periods         : periods used for estimation
:param exclude_periods : periods to be excluded from estimation
:param in_place        : if True then replace the current time series
:return                : the detrended time series
:note                  : outliers from Gts.outliers are ommitted in the estimation and
offsets given Gts.offsets_dates are estimated simultaneously


#### detrend_seasonal_median(wl=11, in_place=False, verbose=False)
Calculates a velocity using the median of pair of displacements exactly separated by one year, inspired from MIDAS and then removes repeating yearly signal
If the time series has less than three years of data, then the time series is kept untouched.


#### differentiate()
differentiate the current time series


* **Returns**

    the differentiated time series as a new Gts object


:note : differentiation is made on .data. .data_xyz is set to None.


#### displacement(sdate=None, edate=None, window=None, method='median', speriod=[], eperiod=[], rounding='day', verbose=True)
Calculates displacements between two dates or two periods


* **Parameters**

    
    * **sdate** – start date in decimal year


    * **edate** – start date in decimal year


    * **window** – time window in days for searching available dates


    * **method** – method to calculate the position. ‘median’ or ‘mean’. default is ‘median’.


    * **speriod** – period for calculating the start position


    * **eperiod** – period for calculating the end position


    * **rounding** – rounding for dates. Choose among ‘day’,’hour’,’minute’ or ‘second’. default is ‘day’.


    * **verbose** – verbose mode



* **Returns**

    displacement as np.array([dn,de,du,sdn,sde,sdu])



#### edge_filter(lbda, in_place=False, verbose=True)
Edge Gts filter using a L1 total variation filter.
The signal is assumed to be piecewise constant.


* **Parameters**

    
    * **lbda** – lambda parameter


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



* **Reference**

    [https://github.com/albarji/proxTV](https://github.com/albarji/proxTV)



#### estimate_local_offset(window_length=4, in_place=False)
Estimate the local offset, just used window_length positions before & window_length positions behind of offset
output: amplitude of local offsets


#### exclude_periods(lperiod, in_place=False, verbose=False)
exclude periods of a Gts


* **Parameters**

    
    * **lperiod** – a list [start_date,end_date] or a list of periods e.g. periods=[[2000.1,2003.5],[2009.3,2010.8]]


    * **in_place** – if True, will make change in place, if False, return s a new time series



* **Note 1**

    X0,Y0,Z0 attributes will be changed if necessary



* **Note 2**

    handles both .data and .data_xyz



#### extract_dates(dates, tol=0.05, in_place=False, verbose=True)
Returns a time series extracted for a given list of dates


* **Parameters**

    
    * **dates** – dates either as a list or  1D numpy array of decimal dates


    * **tol** – date tolerance in days to assert that two dates are equal (default 0.05 day)


    * **in_place** – if True, will make change in place, if False, return s a new time series


    * **verbose** – boolean, verbose mode



#### extract_ndates_after_date(date, n, verbose=False)
Extract n values after a given date
If n values are not available, returns all available values after date
.data is set to None if no value at all is available


* **Parameters**

    
    * **date** – date in decimal year


    * **n** – number of observations to be extracted



* **Returns**

    a new Gts



#### extract_ndates_around_date(date, n)
Extract n values before and n values after a given date
If n values are not available, returns all available values
.data is set to None if no value at all is available


* **Parameters**

    
    * **date** – date in decimal year


    * **n** – number of observations to be extracted



* **Returns**

    a new Gts



#### extract_ndates_before_date(date, n, verbose=False)
Extract n values before a given date
If n values are not available, returns all available values before date
.data is set to None if no value at all is available


* **Parameters**

    
    * **date** – date in decimal year


    * **n** – number of observations to be extracted



* **Returns**

    a new Gts



#### extract_periods(lperiod, in_place=False, verbose=False)
extract periods of a Gts


* **Parameters**

    
    * **lperiod** – a list [start_date,end_date] or a list of periods e.g. periods=[[2000.1,2003.5],[2009.3,2010.8]]


    * **in_place** – if True, will make change in place, if False, return s a new time series



* **Note 1**

    X0,Y0,Z0 attributes will be changed if necessary



* **Note 2**

    handles both .data and .data_xyz



#### find_large_uncertainty(sigma_thresold=10, verbose=True, lcomponent='NE')
Find dates with large uncertainty and flag them as outliers.


* **Parameters**

    
    * **sigma_threshold** – value (mm) for a date to be flagged.


    * **verbose** – verbose mode


    * **lcomponent** – list of components to be checked. default = ‘NE’



#### find_offsets(threshold=3, n_max_offsets=9, conf_level=95, lcomponent='NE', verbose=True, in_place=False)
A simple empirical procedure to find offsets.


* **Parameters**

    
    * **threshold** – threshold value for offset preliminary detection


    * **n_max_offset** – maximum number of offsets to be detected simultaneously


    * **conf_level** – confidence level for a suspected offset to be accepted


    * **lcomponent** – components used for offset detection



* **Returns**

    a new Gts instance with offsets_dates and outliers now populated



#### find_offsets_edge_filter(threshold=0.6, search_lbda=[3, 5, 7, 10, 20, 50, 100, 200, 300], delta_day=100, in_place=False, lcomponent='NE', verbose=True, debug=True, log=False, eq_file=None)

#### find_offsets_t_scan(threshold=0.8, window=250, in_place=False, lcomponent='NE', verbose=True, debug=True)

#### find_outlier_around_date(date, conf_level=95, n=3, lcomponent='NE', verbose=True)
Find an outlier around a given date 
returns the index of the outlier, returns [] if no outlier found
:param date       : given date
:param conf_level : confidence level for F_ratio test of outlier significance (default 95%%)
:param n          : number of dates either sides of date (default n=3)
:param lcomponent : components ‘N’,’E’,’U’,’NE’,’NEU’ (default ‘NE’)


#### find_outliers_and_offsets_through_differentiation(th=100)
find outliers and offsets using differenciation


#### find_outliers_by_RMS_ts(ndays=7, th_detection=5, th_rejection=2)
Find index of outliers in a time series, populate self.outliers.

    
    * rms time series are first calculated over ndays


    * time windows are kept for further inspection if rms(t) > th_detection \* median(rms(ts))


    * for each anomalous time windows, differentiate positions, find the max


    * test whether it is a true outlier (differentiated(t) > th_rejection \* median(differentiated))

output:

    None


#### find_outliers_by_residuals(threshold=5, model='detrend_seasonal', component='NE', in_place=False)
Find index of outliers by trendline/trendline_annual/trendline_seasonal (the complete model)
Then the outliers are detected if their residuals are greater than th_rejection\*standard_deviation

output:

    Add the list of outlier index into self.outliers


#### find_outliers_percentage(percentage=0.03, in_place=False, verbose=False, component='NEU', periods=None, excluded_periods=None)
detrend a time series and
ranks the residuals by increasing absolute value
populate the outliers with the x % largest ones on each component


#### find_outliers_simple(threshold=100, window_length=10, in_place=False, verbose=False, component='NEU', periods=None, excluded_periods=None)

#### find_outliers_sliding_window(threshold=3, in_place=False, verbose=True, periods=[[]], excluded_periods=[[]], component='NE', window_len=15, automatic=True)
Find outliers using sliding windows


#### find_outliers_vondrak(threshold=10, fc=2.0, in_place=False, verbose=True, periods=[[]], excluded_periods=[[]], component='NE')
Find outliers using a Vondrak filter


#### find_time_offsets(option=None, ndays=7, th_detection_rms=3, th_detection_offset=3)
> Find the time of suspected offsets by rms time series calculated over ndays
> Then check the time of offsets: if one offset is too small/None then it is removed
> input:


* ndays: number of positions in the windows. rms time series are calculated over ndays.


* th_detection_rms: the threshold for detecting the anomalous windows rms(t) > th_detection_rms\*median(rms(ts)).


* th_detection_offset: the threshold for detecting the offsets,

    for each anomalous time windows, differentiate positions
    then test whether it is a suspected offset (differentiated(t) > threshold \* median(differentiated))

> output:

> > add the time of offsets in to self.offsets


#### force_daily(in_place=False)
force a time series to be daily with dates at 12:00:00 of every day


#### frame(frame=None, in_place=False, verbose=False)
Rotates a time series according to an Euler pole
Returns a new Gts instance


#### get_coseismic(eq_date, window_days=5, sample_after=1, method='median', in_place=False)
Get coseismic displacement at a given date.
Coseismic displacement is estimated as the position difference between the median of window_days before 
the earthquake date and the median of sample_after samples after the earthquake date.

note: only median method implemented


#### get_unr(site, verbose=False)
Get a time series from [http://geodesy.unr.edu/gps_timeseries/txyz/IGS14/](http://geodesy.unr.edu/gps_timeseries/txyz/IGS14/) in PYACS


* **Parameters**

    
    * **site** – 4-letters code


    * **verbose** – verbose mode



#### info(info=2)
Print various informations about the time series


#### insert_gts_data(gts, in_place=False, verbose=False)
insert data (and/or) .data_xyz of a gts into the current gts


* **Parameters**

    
    * **gts** – tie series to be inserted


    * **in_place** – boolean, if True add_obs to the current Gts, if False, returns a new Gts


    * **verbose** – verbose mode


:return : new Gts or the modified Gts if in_place


#### local_offset_robust(date, n, verbose=False, debug=False)
estimate a local offset (no velocity) with a robust method


* **Parameters**

    
    * **date** – date in decimal year


    * **n** – number of dates before and after the dates used in the estimation


:return : a 1D numpy array with [date, north, east, up, s_north, s_east, s_up]


* **Note**

    the offsets are estimated using the difference between the median position before and after the earthquake using i days


for all i <=n. Then the median of the estimates is returned.


#### make_dynamic_apr(apr, time_step=30.0, pos_tol=0.03, dates=[], gap=20.0, verbose=False)
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



#### make_model(option='detrend', method='L2', loutlier=None, in_place=False)
Estimate time series model parameters using least squares 
input: data: Gts format
option are: ‘detrend’/’detrend_annual’/’detrend_seasonal’
output: new Gts object: time series is now the residuals wrt to the model and its associated values (vel, annual, semi-annual etc)


#### median_filter(n, in_place=False, verbose=True)
returns a filtered time series using scipy.signal.medfilt


* **Parameters**

    
    * **n** – size of the median filter window (must be odd)


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



* **Note**

    the filter is applied to .data and .data_xyz is set to None



#### minimum_component(mask_period=[], p=1, fcut=None, Q=None, in_place=False, verbose=True)
Minimum component filtering for Gts.

Minimum component filtering is useful for determining the background
component of a signal in the presence of spikes


* **Parameters**

    
    * **mask_periods** – periods (list or list of lists) which should be ignored for smoothing


    * **p** – integer (optional). polynomial degree to be used for the fit (default = 1)


    * **fcut** – float (optional). the cutoff frequency for the low-pass filter.  Default value is f_nyq / sqrt(N)


    * **Q** – float (optional). the strength of the low-pass filter.  Larger Q means a steeper cutoff. default value is 0.1 \* fcut


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



* **Note**


This code follows the procedure explained in the book
“Practical Statistics for Astronomers” by Wall & Jenkins book, as
well as in Wall, J, A&A 122:371, 1997


#### mmodel()
Generates a modeled time series from the parameters read in self


#### neu2xyz(corr=False, verbose=False)
populates .data_xyz from .data
requires X0,Y0,Z0 attributes to be set


* **Parameters**

    
    * **corr** – if True, then standard deviation and correlations will also be calculated


    * **verbose** – verbose mode



#### np_datetime_2_eq_time(leap_sec=0.0, eq_time=0.0)
takes a hash of python datetime.datetime object and return a numpy array of seconds with respect to eq_time
if the input array is in GPS time, providing leap_sec correct for the GPS_time - UTC delta


* **Parameters**

    
    * **leap_sec** – number of seconds between GPS_time - UTC delta (leap_sec=17 that is GPS is ahead of UTC by 17 seconds on 13/02/2016)


    * **eq_time** – time of earthquake as a python datetime.datetime object (in UTC)



#### np_yyyy_mm_dd_hh_mm_ss_2_datetime()
converts a numpy array including year month mday hour minute sec to an array of python datetime.datetime object
returns a hash


#### np_yyyy_mm_dd_hh_mm_ss_2_decyear()
converts a numpy array including year month mday hour minute sec to decimal year
returns a 1D array


#### plot(title=None, loffset=True, loutliers=True, verbose=False, date=[], yaxis=None, yupaxis=None, xticks_minor_locator=1, lcomponent=['N', 'E', 'U'], error_scale=1.0, lperiod=[[]], lvline=[], save_dir_plots='.', save=None, show=True, unit='mm', date_unit='decyear', date_ref=0.0, center=True, superimposed=None, lcolor=['r', 'g', 'c', 'm', 'y', 'k', 'b'], label=None, legend=False, set_zero_at_date=None, grid=True, plot_size=None, info=[], xlabel_fmt=None, \*\*kwargs)
Create a plot of a North-East-Up time series and related info (offsets, outliers) using Matplotlib
Coordinates of the time series are assumed to be in meters
default plots units will be mm; Use unit=’m’ to get meters instead


* **Parameters**

    
    * **title** – string to be added to the site name as a plot title


    * **loffset** – boolean
    print a dash vertical line at offset dates


    * **loutliers** – boolean
    print outliers


    * **verbose** – boolean
    verbose mode


    * **date** – [sdate,edate]
    start and end date for plots
    sdate and edate in decimal years if date_unit is either ‘decyear’ or ‘cal’, or in days if date_unit is ‘days’


    * **yaxis** – [min_y,max_y]
    min and max value for the yaxis
    if not provided automatically adjusted


    * **yupaxis** – same as yaxis but applies to the up component only


    * **xticks_minor_locator** – where xticks_minor_locator will be placed. Float when date_unit is ‘decyear’ or ‘days’, a string ‘%Y’,’%m’,’%d’ is date_unit is ‘cal’.


    * **lcomponent** – list of components to be plotted (default =[‘N’,’E’,’U’])


    * **error_scale** – scaling factor for error bars (default = 1.0, 0 means no error bar)


    * **lperiod** – list of periods to be drawn in background (color=light salmon)


    * **lvline** – list of dates where vertical lines will be drawn in background (color=green)


    * **save_dir_plots** – directory used for saving the plots


    * **save** – name, save the plot into name, if simply True an automatic name is given


    * **show** – boolean, is True show the plot


    * **unit** – ‘m’,’cm’,’mm’, default=’mm’


    * **date_unit** – ‘decyear’ or ‘cal’ or ‘days’, default=’decyear’


    * **date_ref** – reference date, default=0.0


    * **center** – boolean, if True the y_axis is centered around the mean value for the plotted period


    * **superimposed** – if a gts is provided, it is superimposed to the master, default=None


    * **lcolor** – color list used for the superimposed time series, default=[‘r’,’g’,’c’,’m’,’y’,’k’,’b’]


    * **label** – label for superimposed time series to be displayed in legend, default=None


    * **legend** – boolean. Set true to display label for superimposed time series, default=False


    * **set_zero_at_date** – date at which the master and superimposed gts will be equal (default=None). date can also be a list with [date,offset_north,offset_east,offset_up]


    * **plot_size** – plot size as a tuple. Default, best guess.


    * **grid** – boolean


    * **info** – title to appear in time series subplots


    * **\*\*kwargs** – any argument to be passed to  matplotlib.pyplot.errorbar




* **Note**

    The list of kwargs are:


{  ‘linewidth’ : 0,       ‘marker’ : marker_main_symbol ,       ‘markersize’ : marker_main_size,        ‘markerfacecolor’ : marker_main_color,       ‘markeredgecolor’ : marker_main_color,       ‘markeredgewidth’ : marker_main_colorlw,       ‘ecolor’ : error_bar_color,       ‘elinewidth’ : error_bar_linewidth,       ‘capsize’ : error_bar_capsize }


#### pwlf(component, n, in_place=False, verbose=False, output=False)
Perform a piecewise approximation of a time series. Since it the routine is 1D, the component E,N, or U needs to be specified.


* **Parameters**

    
    * **component** – component used for the decomposition. Must be ‘E’,’N’ or ‘U’


    * **n** – number of segments


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Output**

    if False, the predicted time series is returned. If True, then a list of dates is returned.



#### read_cats_file(idir='.', ifile=None, gmt=True, verbose=False)
Read cats files in a directory and actually loads the time series


#### read_eq_rename(eq_rename, in_place=False, verbose=False)
Reads the information for the current site (code) from an eq_rename globk file.

Populates loutliers and offsets_dates
Found excluded periods in the eq_rename file are added to loutliers


* **Parameters**

    
    * **eq_rename** – eq_rename (globk format) file to be read


    * **in_place** – boolean. If True then the Gts instance is modified, if False the Gts instance is preserved and a new Gts instance is return


    * **verbose** – verbose mode (boolean)



* **Returns**

    Gts instance



#### read_kenv(ifile, date_type='jd')
Read kenv file (magnet) format for time series


#### read_lon_lat(gmt_file, verbose=False)
Reads a gmt psvelo file and populates Gts.lon & Gts.lat


* **Parameters**

    
    * **gmt_file** – gmt psvelo file


    * **verbose** – verbose mode (boolean)



* **Returns**

    the current Gts instance



#### read_mb_file(idir='.', ifile=None, gmt=True, verbose=False)
Read GAMIT/GLOBK mb_files in a directory and actually loads the time series


#### read_offset_dates(offset_file)
Reads an offset file and populates offsets_dates (pyacs format) attribute of the current Gts instance.
format is simply a code dates. dates can be any format read by pyacs.guess_date


* **Parameters**

    **offset_file** – offset_file to be read



* **Returns**

    the current Gts instance



#### read_pos(tsdir='.', tsfile=None, xyz=True, verbose=False)
Read GAMIT/GLOBK PBO pos file in a directory and actually loads the time series


* **Parameters**

    
    * **tsdir** – directory of pos file


    * **tsfile** – pos file to be loaded


    * **xyz** – reads xyz sx sy sz corr_xy corr_xz corr_yz columns


    * **verbose** – verbose mode



* **Return Nothing**



* **Raises**

    **Nothing** – 



* **Note**

    Since a pos file includes (almost) all the information, data, code, X0,Y0,Z0,t0 will be populated


If file=None, then read_pos will look for a file named CODE\*.pos


#### read_pride(tsdir='.', tsfile=None, xyz=True, verbose=False)
Read PRIDE-PPPAR kinematic result file


* **Parameters**

    
    * **tsdir** – directory of pride-pppar kinematic files


    * **tsfile** – pride-pppar kinematic file to be loaded


    * **verbose** – verbose mode



* **Return Nothing**



* **Raises**

    **Nothing** – 


If file=None, then read_pride will look for a files named kin_\*code


#### read_pride_pos(tsdir='.', tsfile=None, verbose=False)
Read PRIDE-PPPAR static result file


* **Parameters**

    
    * **tsdir** – directory of pride-pppar pos static files


    * **tsfile** – pride-pppar pos static file to be loaded


    * **verbose** – verbose mode


If file=None, then read_pride will look for a files named pos_\*code


#### read_tdp(idir='.', ifile=None, gmt=True, verbose=False)
Read tdp (Gipsy kinematics provided by Cedric Twardzik 17/04/2018) format for time series


#### read_track_NEU(tsdir='.', tsfile=None, leap_sec=0.0, eq_time=None, verbose=False)
Read a GAMIT/GLOBK Track output file generated with the option out_type NEU
in this case dates are seconds
by default the seconds are with respect to the first epoch of measurements
If option leap_sec is provided with a value > 0.0, then GPS time is corrected for the difference between GPTS time and UTC 
If eq_time is provided, it is assumed to be UTC. Expected format is YYYY:MM:MD:HH:MM:SS.S


#### realistic_sigma(option='tsfit', in_place=False, verbose=False)
Calculates realistic sigmas on velocity components
:param option:

> 
> * tsfit: globk T. Herring realistic sigma


> * cats_pl: CATS estimates with noise type estimated (i.e. –model=pl:)


> * cats_seasonal_pl: CATS estimates with seasonal terms and noise type estimated (i.e. –model=pl: –sinusoid=1y1)


> * cats_flicker: CATS estimates assuming flicker noise (i.e. –model=pl:k-1)


> * cats_seasonal_flicker: CATS estimates with seasonal terms and assuming flicker noise (i.e. –model=pl:k-1 –sinusoid=1y1)


#### remove_outliers(periods=None, in_place=False)
removes outliers provided in self.outliers
return a new Gts without the outliers
if in_place = True then self has the outliers removed as well (in _place)


#### remove_pole(pole, pole_type='euler', in_place=False, verbose=True)
remove velocity predicted by an Euler pole or a rotation rate vector from a time series
pole is a 1D array with 3 values
requires self.lon & self.lat attributes to have been filled before 
if in_place = True then replace the current time series


#### remove_velocity(vel_neu, in_place=False)
remove velocity from a time series
vel_neu is a 1D array of any arbitrary length, but with the velocities (NEU) to be removed in the first 3 columns
if in_place = True then replace the current time series


#### reorder(verbose=False)
reorder data and/or data_xyz by increasing dates
always in place


* **Parameters**

    **verbose** – verbose mode



#### rotate(angle, in_place=False)
rotates the axis by an angle


* **Parameters**

    **angle** – angle in decimal degrees clockwise


if in_place = True then replace the current time series


#### save_apr(apr, epoch=None, verbose=False, excluded_periods=None)
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



#### save_eq_rename(eq_rename, verbose=False, excluded_periods=None)
save results of a Gts analysis in globk format eq_rename


* **Parameters**

    
    * **eq_rename** – output eq_rename file (Golbk format)


    * **verbose** – verbose mode (boolean)


    * **exluded_periods** – periods to be excluded



* **Returns**

    Gts instance



#### save_offsets(ofile, verbose=True, comment='', up=False, info=False)
Appends offsets values to a given text file (gmt psvelo format)


* **Parameters**

    
    * **ofile** – output offset file


    * **verbose** – verbose mode (boolean)


    * **comment** – comment as a string. ‘# ‘ is pre-prended to comment if not provided


    * **up** – boolean. If True, then Ve, SVe and SVen are set to 0 and Vu and Vu are written as 4-th and 6-th fields



* **Returns**

    the current Gts instance



#### save_velocity(gmt_file, verbose=True, comment=None, up=False)
Appends velocity estimates (with uncertainties) to a gmt psvelo file


* **Parameters**

    
    * **gmt_file** – output gmt psvelo file (will append if gmt_file already exists)


    * **verbose** – verbose mode (boolean)


    * **comment** – comment as a string. ‘# ‘ is pre-prended to comment if not provided


    * **up** – boolean. If True, then Ve, SVe and SVen are set to 0 and Vu and Vu are written as 4-th and 6-th fields



* **Returns**

    the current Gts instance



#### savitzky_golay(in_place=False, verbose=True, window_length=15, polyorder=3, deriv=0, delta=1.0, mode='interp', cval=0.0)
returns a filtered time series using scipy.signal.savgol_filter

See documentation for the filter parameters.
[http://https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html#scipy.signal.savgol_filter](http://https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html#scipy.signal.savgol_filter)


* **Parameters**

    
    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



#### set_zero_at_date(date, offset=None, in_place=False)
make a translation of a time series, setting to 0 at a given date
if the provided date does not exist, uses the next date available


* **Parameters**

    
    * **date** – date in decimal year


    * **offset** – an offset (in mm) to be added. Could be a float, a list or 1D numpy array with 3 elements



#### sigma_cats(in_place=False, verbose=False, k='k-1', seasonal='')
runs CATS for getting realistic sigma


#### sigma_vel_tsfit(in_place=False, verbose=False)
runs tsfit for getting realistic sigma


#### smooth(window_len=11, window='hanning', in_place=False, verbose=False, component='NEU')
smooth a time series


#### spline(smoothing=1, degree=5, date=None)

* **Parameters**

    **smoothing** – Positive smoothing factor used to choose the number of knots. Number of knots will be increased


until the smoothing condition is satisfied:

sum((w[i] \* (y[i]-spl(x[i])))\*\*2, axis=0) <= s


* **Parameters**

    
    * **degree** – Degree of the smoothing spline. Must be <= 5. Default is k=3, a cubic spline.


    * **date** – 1D array of interpolation dates in decimal year, or ‘day’ for every day. defualt None will interpolate


at data date only.
:return: new gts instance


#### substract_ts(ts, tol=0.05, verbose=True)
substract the ts provided as argument to the current time series


* **Parameters**

    
    * **ts** – time series to be substracted as a Gts instance


    * **tol** – date tolerance to decide whether two dates are identical in both time series. default = 1/4 day


    * **verbose** – verbose mode


:return : new Gts


#### substract_ts_daily(ts, verbose=True)
substract the ts provided as argument to the current time series


* **Parameters**

    
    * **ts** – time series to be substracted as a Gts instance


    * **verbose** – verbose mode


:return : new Gts


* **Note**

    this method assumes daily time series



#### suspect_offsets(threshold=3, verbose=True, lcomponent='NE', n_max_offsets=10, in_place=False)
Tries to find offsets in a time series


#### suspect_offsets_mf(threshold=3, verbose=True, lcomponent='NE', n_max_offsets=5, in_place=False, debug=False)
Tries to find offsets in a time series using a median filter


#### test_offset_significance(date, conf_level=95, lcomponent='NE', verbose=True, debug=False, mode='local')
test the significance of an offset


* **Param**

    date        : date of the offset to be tested



* **Param**

    conf_level  : confidence level in percent (default=95)



* **Param**

    lcomponent  : component to be tested (default=’NE’)



* **Param**

    mode        : choose among ‘local’,’detrend’,’detrend_seasonal’ to test significance



* **Param**

    verbose     : verbose mode



* **Returns**

    : True if significant, else False



#### test_offsets(verbose=False, debug=True, window_length=None)
Test the offset:

    
    * delete the small offset (1mm for East/North, 2mm for Up)


    * then make a F ratio test


    * re-check to delete the small offsets


#### to_pandas_df()

* **Parameters**

    **self** – 



* **Returns**

    pandas DataFrame



* **Note**

    uncertainties are not imported.



#### trajectory(model_type, offset_dates=[], eq_dates=[], H_fix={}, H_constraints={}, H_bounds={}, component='NEU', verbose=False)
Calculates the parameters of a (non-linear) trajectory model for a Geodetic Time Series.
The trajectory model is:

y(t) =

trend : trend_cst + trend \* ( t - t0 ) +

annual: a_annual \* cos( 2\*pi + phi_annual ) +

semi-annual: a_semi_annual \* cos( 2\*pi + phi_semi_annual ) +

offset : Heaviside( t - t_offset_i ) \* offset_i +

post-seismic_deformation as decaying log (psd_log):   psd_eq_i \* np.log( 1 + Heaveside( t - eq_i )/tau_i )


* **Parameters**

    **model_type** – string made of the key-word the parameters to be estimated.


Key-word parameters are

‘trend’,’annual’,’semi-annual’,’seasonal’,’offset’,’psd_log’.

‘trend-seasonal-offset-psd_log’ will do the full trajectory model.


* **Parameters**

    
    * **offset_dates** – a list of offset_dates in decimal year


    * **eq_dates** – a list of earthquake dates for which post-seismic deformation (psd_log) will be estimated


    * **H_fix** – a dictionary including the name of the parameter to be hold fixed and the value.


For instance to impose the co-seismic offset (North-East-Up) and relaxation time of 100 days for the
first earthquake use:

H_fix = { ‘psd_log_offset_00’:[10., 15., 0.] , ‘psd_log_tau_00’:[100., 100., 100.]}


* **Parameters**

    **H_constraints** – a dictionary including the name of the parameter to be constrained.


For instance to impose a 50 days constraints around 500 days
on the relaxation time of the second earthquake for all NEU components use: H_fix = { ‘psd_log_tau_01’:[[500.,50],
[500.,50] , [500.,50]]}


* **Parameters**

    **H_bounds** – a dictionary including the bounds.


For instance to impose a relaxation time for the third earthquake to be in the range
of 2 to 3 years, for all NEU components use: H_bounds = { ‘psd_log_tau_02’:[[2\*365.,3\*365.], [[2\*365.,3\*365.] ,
[[2\*365.,3\*365.]]}


* **Parameters**

    
    * **component** – string , component for which the trajectory model will be estimated.


    * **verbose** – verbose mode



* **Note**

    Unlike most pyacs.gts functions, trajectory returns 4 elements: the results as a dictionary, the model Gts,


the residual Gts and a Gts with model predictions at every day.


#### tv_l2_filter(lbda, in_place=False, verbose=True)
Gts filter using a L2 total variation filter.
The signal is assumed to be detrended.


* **Parameters**

    
    * **lbda** – lambda parameter


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



* **Reference**

    [https://github.com/albarji/proxTV](https://github.com/albarji/proxTV)



#### vondrak(fc, in_place=False, verbose=True, component='NEU')
returned a filtered Gts using a Vondrak filter


* **Parameters**

    
    * **fc** – cutoff frequence in cycle per year


    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



#### wiener(in_place=False, verbose=True, my_size=15, noise=None)
returns a filtered time series using scipy.signal.wiener

See documentation for the filter parameters.


* **Parameters**

    
    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series



#### write_cats(idir, offsets_dates=None, add_key='')
Writes a file for a cats analysis
if offsets_dates is not None then offsets are added at the beginning of the file


#### write_mb_file(idir, add_key='')

#### write_pos(idir, add_key='', force=None, verbose=False)
Write a time series in GAMIT/GLOBK PBO pos format


* **Parameters**

    
    * **idir** – output directory


    * **add_key** – if not blank then the output pos file will be CODE_add_key.pos, CODE.pos otherwise.


    * **force** – set force to ‘data’ or ‘data_xyz’ to force pos to be written from .data or .data_xyz



* **Note1**


default behaviour (force = None)
if data and data_xyz are not None, then print them independently
if there are data only, then uses X0,Y0,Z0 to write data_xyz
if there are data_xyz only, recreate data and write it


#### wrms()
Return the wrms


* **Return wrms**

    return(np.array([wrms_n,wrms_e,wrms_up]))



#### xyz2neu(corr=False, ref_xyz=None, verbose=False)
populates neu (data) using xyz (data_xyz)
lon, lat and h will also be set.


* **Parameters**

    
    * **corr** – if True, then standard deviation and correlations will also be calculated


    * **ref_xyz** – [X,Y,Z] corresponding to the 0 of the local NEU frame. If not provided, the first position is used as a reference


    * **verbose** – verbose mode



* **Note**

    this method is always in place
