---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.gts_dates
images: {}
path: /pyacs-gts-lib-gts-dates
title: pyacs.gts.lib.gts_dates module
---

# pyacs.gts.lib.gts_dates module

This module gathers a few useful date functions, which can be used to read different time series formats.
pyacs.pygts uses decimal year as time defaults. Seconds for High-Rate GPS solution can also be used.


### pyacs.gts.lib.gts_dates.np_yyyy_mm_dd_hh_mm_ss_2_decyear(data)
converts a numpy array including year month mday hour minute sec to decimal year
returns a 1D array


### pyacs.gts.lib.gts_dates.np_yyyy_mm_dd_hh_mm_ss_2_datetime(data)
converts a numpy array including year month mday hour minute sec to an array of python datetime.datetime object
returns a hash


### pyacs.gts.lib.gts_dates.np_datetime_2_eq_time(data, leap_sec=0.0, eq_time=0.0)
takes a hash of python datetime.datetime object and return a numpy array of seconds with respect to eq_time
if the input array is in GPS time, providing leap_sec correct for the GPS_time - UTC delta


* **Parameters**

    
    * **leap_sec** – number of seconds between GPS_time - UTC delta (leap_sec=17 that is GPS is ahead of UTC by 17 seconds on 13/02/2016)


    * **eq_time** – time of earthquake as a python datetime.datetime object (in UTC)



### pyacs.gts.lib.gts_dates.decyear2days(self, ref_date='', in_place=False)
Converts the dates of a time series from decimal years to days after a reference date
ref_date is read by guess_date
