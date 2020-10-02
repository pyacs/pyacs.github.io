---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.astrotime
images: {}
path: /pyacs-lib-astrotime
title: pyacs.lib.astrotime module
---

# pyacs.lib.astrotime module

AstroTime.py is a traduction from perl module Astro::Time distributed by CPAN 
and written by Chris Phillips (Chris.Phillips@csiro.au). Conversion to python made by Jean-Mathieu Nocquet (Geoazur - CNRS-IRD-OCA-Univ. Nice, nocquet@geoazur.unice.fr)

AstroTime contains a set of Python routines for time based
conversions, such as conversion between calendar dates and Modified
Julian day and conversion from UT to local sidereal time. Included are
routines for conversion between numerical and string representation of
angles. All string functions removed.

Conversion from and to datetime objects have also been added for convenience.


* **note**

    This module is intended dates manipulation, but leap seconds for instance are not handled.        See the GPSTime module for GPS, UTC times conversions.



* **note**

    python 3.6 : all / operator changed to // to force integer operations



* **warning**

    !!! all conversions not specifying ut or uts use 12h00mn00s as a default. ut is the decimal fraction of day
    and uts is the number of seconds since 00h00m00.0s



### pyacs.lib.astrotime.cal2dayno(day, month, year)
Returns the day of year (doy).


* **Parameters**

    **day****,****month****,****year** – 



* **Type**

    int,int,int



* **Returns**

    doy of year as int



* **Example**


```python
>>> import pyacs
>>> pyacs.cal2dayno(01,01,2000)
>>> 1
>>> pyacs.cal2dayno(29,02,2000)
>>> 60
>>> pyacs.cal2dayno(29.,02,2000)
>>> 60.
>>> pyacs.cal2dayno(29,02,2001)
>>> !!!  29  out of range
>>> !!! bad day
```


### pyacs.lib.astrotime.cal2mjd(day, month, year, ut=0.5)
Converts a calendar date (universal time) into modified Julian day number.
mjd     Modified Julian day (JD-2400000.5)


* **Parameters**

    **month****, ****year** (*day**,*) – 


:param ut : day fraction ([0.,1.[)
:returns: mjd (modified Julian day (julian day -2400000.5))
:rtype: float
:note: Be aware that when ut is not provided, then the middle of the day is used. See example.


* **Example**


```python
>>> import pyacs
>>> pyacs.cal2mjd(29,02,2000)
>>> 51603.5
>>> pyacs.cal2mjd(29,02,2000,ut=0.0)
>>> 51603.0
```


### pyacs.lib.astrotime.cal2decyear(day, month, year, ut=0.5)
converts a calendar date to decimal year


* **Parameters**

    **month****, ****year** (*day**,*) – 


:param ut : day fraction ([0.,1.[)
:returns: decimal year
:rtype: float
:note: Be aware that when ut is not provided, then the middle of the day is used.


### pyacs.lib.astrotime.cal2datetime(day, month, year, ut=0.5)
converts a calendar date to a datime python instance


* **Parameters**

    **month****, ****year** (*day**,*) – 


:param ut : day fraction ([0.,1.[), optional

:note:!!! the returned datetime is at 12:00, that is ut=0.5 by default


### pyacs.lib.astrotime.dayno2cal(dayno, year)
Returns the day and month corresponding to dayno of year.


* **Parameters**

    **year** (*dayno**,*) – 



* **Returns**

    day, month



### pyacs.lib.astrotime.dayno2mjd(dayno, year, ut=0.5)
converts a dayno and year to modified Julian day


* **Parameters**

    
    * **year** (*dayno**,*) – 


    * **ut** – day fraction, optional



* **Returns**

    modified Julian day (julian day - 2400000.5)



* **Note**

    Be aware that when ut is not provided, then the middle of the day is used. See example.



* **Example**


```python
>>> import pyacs
>>> pyacs.dayno2mjd(60,2000)
>>> 51603.5
>>> pyacs.dayno2mjd(60.,2000,ut=0)
>>> 51603.0
```


### pyacs.lib.astrotime.dayno2decyear(dayno, year, ut=0.5)
converts julian day to decimal year


* **Parameters**

    
    * **year** (*dayno**,*) – 


    * **ut** – day fraction, optional



* **Returns**

    decimal year



* **Note**

    !!! accounts for leap years with 366 days



* **Note**

    !!! unless ut is specified, the returned decimal years is at 12:00, that is ut=0.5 by default



* **Example**


```python
>>> import pyacs
>>> pyacs.dayno2decyear(60,1999)
>>> 1999.16301369863
>>> pyacs.dayno2decyear(60,2000)
>>> 2000.1625683060108
>>> pyacs.dayno2decyear(60,2001)
>>> 2001.16301369863
>>> pyacs.dayno2decyear(60,2001,ut=0.)
>>> 2001.1616438356164
```


### pyacs.lib.astrotime.dayno2datetime(dayno, year, ut=0.5)
julian day to datetime python instance


* **Parameters**

    
    * **year** (*dayno**,*) – 


    * **ut** – day fraction, optional



* **Returns**

    datetime


:note:!!! the returned datetime is at 12:00, that is uts=24.0\*60.0\*60/2.0 by default

:note:!!! specify uts for other time of the day


### pyacs.lib.astrotime.mjd2cal(mjd)
Converts a modified Julian day number into calendar date (universal time). (based on the slalib routine sla_djcl).


* **Parameters**

    **mjd** – modified Julian day (JD-2400000.5)



* **Returns**

    day,month,year,ut



* **Return type**

    int,int,int,float



* **Note**

    ut is the the day fraction in [0., 1.[.



### pyacs.lib.astrotime.mjd2dayno(mjd)
converts a modified Julian day into year and dayno (universal time).


* **Parameters**

    **mjd** – modified julian day



* **Returns**

    dayno,year,ut



* **Return type**

    int,int,float



* **Example**


```python
>>> import pyacs
>>> pyacs.mjd2dayno(51603.0)
>>> (60, 2000, 0.0)
>>> pyacs.mjd2dayno(51603.5)
>>> (60, 2000, 0.5)
```


### pyacs.lib.astrotime.mjd2decyear(mjd)
converts a modified julian day to decimal year conversion


* **Parameters**

    **mjd** – modified julian day



* **Returns**

    decimal year



### pyacs.lib.astrotime.mjd2datetime(mjd)
converts Modified Julian Day date to datime python instance


* **Parameters**

    **mjd** – modified julian day



* **Returns**

    datetime instance



### pyacs.lib.astrotime.mjd2gpsweek(mjd)
converts a modified julian day to gps week and gps day of week


* **Parameters**

    **mjd** – modified julian day



* **Returns**

    gps_week,day_of_week



### pyacs.lib.astrotime.decyear2cal(decyear)
decimal year to calendar date conversion


* **Parameters**

    **decyear** – decimal year



* **Returns**

    day of month,month,ut



* **Note**

    the input decimal year is assumed to account for leap years, that is the day of year is the     decimal of decyear \* number of days in the year.



### pyacs.lib.astrotime.decyear2dayno(decyear)
converts decimal year to the day of year


* **Parameters**

    **decyear** – decimal year



* **Returns**

    day of year,ut



* **Note**

    the input decimal year is assumed to account for leap years, that is the day of year is the     decimal of decyear \* number of days in the year.



### pyacs.lib.astrotime.decyear2mjd(decyear)
decimal year to modified julian day conversion


* **Parameters**

    **decyear** – decimal year



* **Returns**

    modified julian day



### pyacs.lib.astrotime.decyear2datetime(decyear)
converts a decimal date to a datime python instance


* **Parameters**

    **decyear** – decimal year



* **Returns**

    datetime instance



### pyacs.lib.astrotime.decyear2epoch(decyear)
converts decimal year to formatted epoch %02d:%03d:%05d


* **Parameters**

    **decyear** – decimal year


:returns : ‘yy:doy:sec’


* **Note**

    the input decimal year is assumed to account for leap years, that is the day of year is the     decimal of decyear \* number of days in the year.



* **Example**


```python
>>> import pyacs
>>> pyacs.cal2decyear(01,03,2001)
>>> 2001.16301369863
>>> pyacs.dec
>>> pyacs.decyear2epoch(2001.16301369863)
>>> '01:060:43200'
>>> pyacs.decyear2epoch(2000.16301369863)
>>> '00:060:57284'
>>> pyacs.decyear2epoch(pyacs.cal2decyear(01,03,2000))
>>> '00:061:43200'
```


### pyacs.lib.astrotime.datetime_from_calarray(calarray, hour=12, minute=0, sec=0, ms=0)
Build a datetime array from an array of calendar dates


* **Parameters**

    **calarray** – 1D or 2D numpy array. Columns order are year,month,mday,hour,minute,second,microsecond



* **Returns**

    numpy 1D array of datime instances



* **Note**

    year,month,mday are mandatory. If not provided then hour=12, minute=0, sec=0,ms=0 (middle of the day)



### pyacs.lib.astrotime.datetime2cal(datetime)
converts from python datetime to calendar date


* **Parameters**

    **datetime** – datetime instance



* **Returns**

    year,month,monthday,ut



### pyacs.lib.astrotime.datetime2dayno(datetime)
Converts python datetime to dayno,year,ut


* **Parameters**

    **datetime** – pythob datetime instance



* **Returns**

    year,dayno,ut



### pyacs.lib.astrotime.datetime2mjd(datetime)
converts a python datetime instance to a modified julian day


* **Parameters**

    **datetime** – python datetime instance



* **Returns**

    modified julian day



### pyacs.lib.astrotime.datetime2decyear(datetime)
converts a python datetime instance to decimal year


* **Parameters**

    **datetime** – python datetime instance or array of it



* **Returns**

    decimal year



### pyacs.lib.astrotime.datetime_round_second(my_datetime)
rounds a python datetime instance to the nearest second


* **Parameters**

    **datetime** – python datetime instance or array of it



* **Returns**

    new rounded datetime



### pyacs.lib.astrotime.gpsweek2mjd(gpsweek, dow)
converts a GPS week and dow to modified julian day


* **Parameters**

    **gpsweek****,****dow** – gps week, day of week (0 is sunday, 6 saturday)



* **Returns**

    modified julian day



### pyacs.lib.astrotime.epoch2decyear(epoch)
Converts an epoch string used in the SINEX format ‘YY:DOY:SOD’ e.g.’17:100:43185’ into a decimal year


* **Parameters**

    **epoch** – epoch formatted string or list of epochs



* **Returns**

    decimal year or array of decimal years



### pyacs.lib.astrotime.jd2mjd(jd)
Converts a Julian day to a Modified Julian day


* **Parameters**

    **jd** – Julian day



* **Returns**

    jd-2400000.5



### pyacs.lib.astrotime.mjd2jd(mjd)
converts a Modified Julian day to Julian day


* **Parameters**

    **mjd** – Modified Julian day



* **Returns**

    mjd + 2400000.5



### pyacs.lib.astrotime.yr2year(yr)
converts two digits year to four digits year


* **Parameters**

    **yr** – 2-digits year (e.g. 01)



* **Returns**

    4-digit years (2001). This is yr+2000 if yr<80 yr+1900 otherwise.



* **Note**

    This is an heritage from a bad practice in the geodesy community assuming that origin of the universe started with GPS. See example.



* **Example**


```python
>>> import pyacs
>>> pyacs.yr2year(96)
>>> 1996
>>> pyacs.yr2year(11)
>>> 2011
```


### pyacs.lib.astrotime.year2yr(year)
converts 4-digits year to 2-digits year


* **Parameters**

    **yr** – 4-digits year (e.g. 2001)



* **Returns**

    2-digit years (01). This is yr-2000 if yr<80 yr-1900 otherwise.



* **Note**

    This is an heritage from a bad practice in the geodesy community assuming that origin of the universe started with GPS in 1980. See example.



* **Example**


```python
>>> import pyacs
>>> pyacs.year2yr(1996)
>>> 96
>>> pyacs.year2yr(2011)
>>> 11
```


### pyacs.lib.astrotime.leap_year(year)
Returns true if year is a leap year.


* **Parameters**

    **year** – year in YYYY



* **Returns**

    True if year is leap, False otherwise



### pyacs.lib.astrotime.uts2hmsmicros(uts)
converts decimal seconds on a day (0-86400) to hours, min, seconde, microseconds


* **Parameters**

    **uts** – decimal seconds since 00:00:00.0. Must be in the [0.,86400.[ range.



* **Returns**

    hours,minutes,seconds,microseconds



* **Return type**

    int,int,int,float



* **Example**


```python
>>> import pyacs
>>> pyacs.uts2hmsmicros(86399.999999)
>>> (23, 59, 59, 999999.0000069374)
>>> pyacs.uts2hmsmicros(86400)
>>> !!!  86400 uts out of range [0- 86400.0 [
```


### pyacs.lib.astrotime.hmsmicros2uts(h, mn, s=0, microsecond=0)
converts hour minute seconds to uts

:param hours,minutes,seconds,microseconds
:returns: uts


### pyacs.lib.astrotime.hmsmicros2ut(h, mn, s=0, microsecond=0)
converts hour minute seconds to fractional day

:param hours,minutes,seconds,microseconds
:returns: ut


### pyacs.lib.astrotime.ut2uts(ut)
converts fractional day to seconds


* **Parameters**

    **ut** – fractional day in [0.,1.[



* **Returns**

    ut \* 60.\*60.\*24.



### pyacs.lib.astrotime.uts2ut(uts)
converts uts in seconds to fractional day


* **Parameters**

    **uts** – seconds in [0.,86400.[



* **Returns**

    uts / (60.\*60.\*24.)



### pyacs.lib.astrotime.day_since_decyear(decyear, ref_decyear)
Calculates the number of days since a reference date.


* **Parameters**

    **decyear** – decimal year



* **Returns**

    days elapsed since decyear (float)



* **Note**

    negative number means before the reference date



* **Note**

    a useful function for postseismic analysis.



* **Example**


```python
>>> import pyacs
>>> ref_decyear=pyacs.cal2decyear(16,4,2016,ut=pyacs.hmsmicros2ut(23, 58, 33)) # Ecuador, Mw 7.8 EQ
>>> pyacs.day_since_decyear(pyacs.cal2decyear(17,4,2016,ut=pyacs.hmsmicros2ut(23, 58, 32)),ref_decyear)
>>> 0.9999884259232203
>>> pyacs.day_since_decyear(pyacs.cal2decyear(17,4,2016,ut=pyacs.hmsmicros2ut(23, 58, 33)),ref_decyear)
>>> 0.9999999999854481
>>> pyacs.day_since_decyear(pyacs.cal2decyear(16,4,2017,ut=pyacs.hmsmicros2ut(23, 58, 33)),ref_decyear)
>>> 364.9999999999345
>>> ld=pyacs.mjd2decyear(np.arange(pyacs.cal2mjd(13,4,2016),pyacs.cal2mjd(19,4,2016)))
>>> ld
>>> array([ 2016.283,  2016.286,  2016.288,  2016.291,  2016.294,  2016.296])
>>> pyacs.day_since_decyear(ld,ref_decyear)
>>> array([-3.499, -2.499, -1.499, -0.499,  0.501,  1.501])
```


### pyacs.lib.astrotime.guess_date(date)
Tries to guess a date from input parameter
returns a decimal year


* **Parameters**

    **date** – date as string or float



* **Returns**

    decimal year



* **Example**


```python
>>> import pyacs
>>> pyacs.guess_date('2016/04/16')
>>> 2016.2909836065573
```


### pyacs.lib.astrotime.decyear2seconds(np_decyear, rounding='day')
converts decimal year to a seconds since 1980/1/1/0/0/0


* **Parameters**

    **rounding** – controls rounding. ‘day’ means at 12:00:00,


‘hour’ at 00:00, ‘minute’ at the current minute with 00 seconds, ‘second’ at the integer of the current second.
:return: 1D integer (np.int64) numpy array


### pyacs.lib.astrotime.seconds2datetime(seconds)
converts seconds since 1980/1/1/0/0/0 to a datetime object

:return:a 1D numpy array of datetime object
