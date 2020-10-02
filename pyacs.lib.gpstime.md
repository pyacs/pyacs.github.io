---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.gpstime
images: {}
path: /pyacs-lib-gpstime
title: pyacs.lib.gpstime module
---

# pyacs.lib.gpstime module

Note: Leap seconds still needs to be checked an improve
A Python implementation of GPS related time conversions.

Copyright 2002 by Bud P. Bruegger, Sistema, Italy
[mailto:bud@sistema.it](mailto:bud@sistema.it)
[http://www.sistema.it](http://www.sistema.it)

Modifications for GPS seconds by Duncan Brown

PyUTCFromGpsSeconds added by Ben Johnson

This program is free software; you can redistribute it and/or modify it under
the terms of the GNU Lesser General Public License as published by the Free
Software Foundation; either version 2 of the License, or (at your option) any
later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU Lesser General Public License for more
details.

You should have received a copy of the GNU Lesser General Public License along
with this program; if not, write to the Free Software Foundation, Inc., 59
Temple Place, Suite 330, Boston, MA  02111-1307  USA

GPS Time Utility functions

This file contains a Python implementation of GPS related time conversions.

The two main functions convert between UTC and GPS time (GPS-week, time of
week in seconds, GPS-day, time of day in seconds).  The other functions are
convenience wrappers around these base functions.

A good reference for GPS time issues is:
[http://www.oc.nps.navy.mil/~jclynch/timsys.html](http://www.oc.nps.navy.mil/~jclynch/timsys.html)

Note that python time types are represented in seconds since (a platform
dependent Python) Epoch.  This makes implementation quite straight forward
as compared to some algorigthms found in the literature and on the web.


### pyacs.lib.gpstime.dayOfWeek(year, month, day)
returns day of week: 0=Sun, 1=Mon, .., 6=Sat


### pyacs.lib.gpstime.gpsWeek(year, month, day)
returns (full) gpsWeek for given date (in UTC)


### pyacs.lib.gpstime.julianDay(year, month, day)
returns julian day=day since Jan 1 of year


### pyacs.lib.gpstime.mkUTC(year, month, day, hour, minute, sec)
similar to python’s mktime but for utc


### pyacs.lib.gpstime.ymdhmsFromPyUTC(pyUTC)
returns tuple from a python time value in UTC


### pyacs.lib.gpstime.wtFromUTCpy(pyUTC, leapSecs=14)
convenience function:
allows to use python UTC times and
returns only week and tow


### pyacs.lib.gpstime.gpsFromUTC(year, month, day, hour, minute, ssec, leapSecs=30)
converts UTC to: gpsWeek, secsOfWeek, gpsDay, secsOfDay

a good reference is:  [http://www.oc.nps.navy.mil/~jclynch/timsys.html](http://www.oc.nps.navy.mil/~jclynch/timsys.html)

This is based on the following facts (see reference above):

GPS time is basically measured in (atomic) seconds since 
January 6, 1980, 00:00:00.0  (the GPS Epoch)

The GPS week starts on Saturday midnight (Sunday morning), and runs
for 604800 seconds.

Currently, GPS time is 13 seconds ahead of UTC (see above reference).
While GPS SVs transmit this difference and the date when another leap
second takes effect, the use of leap seconds cannot be predicted.  This
routine is precise until the next leap second is introduced and has to be
updated after that.

SOW = Seconds of Week
SOD = Seconds of Day

Note:  Python represents time in integer seconds, fractions are lost!!!


### pyacs.lib.gpstime.UTCFromGps(gpsWeek, SOW, leapSecs=14)
converts gps week and seconds to UTC

see comments of inverse function!

SOW = seconds of week
gpsWeek is the full number (not modulo 1024)


### pyacs.lib.gpstime.GpsSecondsFromPyUTC(pyUTC, _leapSecs=14)
converts the python epoch to gps seconds

pyEpoch = the python epoch from time.time()


### pyacs.lib.gpstime.testTimeStuff()

### pyacs.lib.gpstime.testJulD()

### pyacs.lib.gpstime.testGpsWeek()

### pyacs.lib.gpstime.testDayOfWeek()

### pyacs.lib.gpstime.testPyUtilties()
