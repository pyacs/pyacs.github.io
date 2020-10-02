---
date: '2020-10-02T17:56:24.758Z'
docname: tutorial_gts
images: {}
path: /tutorial-gts
title: Getting started GPS time series
---

# Getting started GPS time series

## Making time series

Assuming that you have a set of sinex files in *mysinex* directory:

```
ls mysinex/*.snx > lsinex
```

and that you have downloaded the following files from your prefered IGS data center:

```
ftp://igs-rf.ign.fr/pub/discontinuities/soln.snx
ftp://igs.ign.fr/pub/igs/products/1883/IGS16P06.ssc.Z
uncompress IGS16P06.ssc.Z
```

You can then run:

```
pyacs_make_time_series.py -lsinex lsinex -experiment run01 -ref_sinex IGS16P06.ssc --discontinuity soln.snx
```

In directory *run01*, you now have the following directories:


* *pos* : directory of time series in GAMIT/GLOBK PBO format


* *res_pos* : directory of residual time series with respect to your reference solution (here *IGS16P06.ssc*)


* *stat* : some statistic of your solution

## Visualizing time series

Run ipyacs.py to enter the pyacs interactive environment:

```
cd run01/pos
ipyacs.py
Python 2.7.10 |Anaconda 2.4.1 (x86_64)| (default, Sep 15 2015, 14:29:08)
Type "copyright", "credits" or "license" for more information.
IPython 4.0.1 -- An enhanced Interactive Python.
?         -> Introduction and overview of IPython's features.
%quickref -> Quick reference.
help      -> Python's own help system.
object?   -> Details about 'object', use 'object??' for extra details.
-- Welcome to pyacs interactive environment -- version  0.01
- Importing pyacs.pygts module
- No mb_files found
- No kenv file found
- No cats file found
=> Reading  QUEM.pos
.
.
=> Reading  TU01.pos
- No Gamit/Globk track NEU file found
- Importing numpy as np
- Importing math
- Importing matplotlib.pyplot as plt
In [1]:
```

pyacs has tried to read everything it could. The resulting loaded time series are stored
in a Sgts (Super Geodetic Time Series) instance called *ts*. Individual Gts (Geodetic Time Series) are
store as attribute of *ts*.

To visualize an individual time series:

```
ts.QUEM.plot()
```

should provide:



![image](_static/ts_quem_raw.png)

### Detrending time series

Detrending is simply achieved applying the detrend() method to the Gts instance ts.QUEM:

```
detrended_QUEM=ts.QUEM.detrended()
detrended_QUEM.plot()
```

## Using pyacs’help

For any function, help is available from the command line of the interactive environment:

```
help(ts.QUEM.plot)
```

Press *q* to exit from the *help* environment.
Selecting a specific period *[2008.0, 2010.0]* and highlighting two periods [[2008.1,2008.7],[2009.6,2009.8]] can be simply obtained:

```
ts.QUEM.plot(date=[2008.0, 2010.0],lperiod=[[2008.1,2008.7],[2009.6,2009.8]])
```

## Chaining methods

In general, a method applied on a Gts instance will return a new Gts so that various methods can be successively applied:

```
ts.QUEM.find_outliers_percentage(percentage=0.005).plot().remove_outliers().plot()
```

The line above does:


* select the 0.5% largest residuals of the detrended time series; returns a new Gts


* plot the returned Gts; returns the Gts


* remove the flagged outliers; returns a new time series with the outliers removed


* plot the new time series

## Automatic analysis

A very basic automatic analysis is provided through the lazy_pyacs method. In order to
visualize how it works, we create a fake time series with offsets:

```
import numpy as np            # import the Numeric Python library
import pyacs.pygts.Gts as Gts # import the Gts class
my_ts=Gts(code='XXXX')        # creates Gts instance for site with code XXXX
my_dates=np.arange(2010.0,2015.0,0.01) # creates a list of dates
ndates=my_dates.shape[0]          # number of dates
data=np.zeros((ndates,7))     # the future data of the XXXX time series
data[:,0]=my_dates                        # populates the dates column vector
data[:,1:]=np.random.normal(0.0,0.001,(ndates,6)) # creates a time series with 0 velocities and 1 mm random noise
lindex=np.where(data[:,0]>2011.0) # get the index of the time series after 2011.0
data[lindex,1]=data[lindex,1]+0.005 # add an offset of 5 mm on the north component after 2011.0
lindex=np.where(data[:,0]>2012.0) # get the index of the time series after 2011.0
data[lindex,2]=data[lindex,2]+0.002 # add an offset of 2 mm on the east component after 2012.0
data[:,4:]=data[:,4:]**2 # standard deviation on the 3 components
my_ts.data=data               # data is now the data of the XXXX time series
my_ts.plot(error_scale=1.0,center=False)   # plot the time series
my_lazy_ts=my_ts.lazy_pyacs() # lazy pyacs analysis
my_detrended_ts=my_lazy_ts.detrend_seasonal() # get the detrended time series with offsets estimated
my_detrended_ts.info() # gets the values of the modeled time series
my_detrended_ts.plot() # plots the resulting time series
print 'Contents of XXXX.eq_rename'
!cat XXXX.eq_rename           # cat the eq_rename created using a system command
```
