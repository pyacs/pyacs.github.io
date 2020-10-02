---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.model
images: {}
path: /pyacs-gts-lib-model
title: pyacs.gts.lib.model module
---

# pyacs.gts.lib.model module


### pyacs.gts.lib.model.add_vel_sigma(self, in_place=False, b_fn=4, verbose=True)
calculates realistic sigma on velocity components assuming white &  
flicker using eq (19) & (23) from Williams (J. of Geodesy, 2003)
b_fn is the value for flicker noise, taken as 4 mm/yr^1/4
model can be detrend, detrend_annual, detrend_seasonal 
if in_place = True then replace the current time series


### pyacs.gts.lib.model.detrend(self, method='L2', in_place=False, periods=[], exclude_periods=[])
detrends a time series and save velocity estimates in velocity attribute

:param periods         : periods used to estimate the velocity
:param exclude_periods : periods to be excluded for the velocity estimate
:param in_place        : if True then replace the current time series
:return                : the detrended time series
:note                  : outliers from Gts.outliers are omitted in the estimation and
offsets given Gts.offsets_dates are estimated simultaneously


### pyacs.gts.lib.model.detrend_annual(self, method='L2', in_place=False, periods=None, exclude_periods=None)
estimates a trend + annual terms in a time series and removes them
velocity and annual attribute are saved in Gts.velocity & Gts.annual

:param periods         : periods used for estimation
:param exclude_periods : periods to be excluded from estimation
:param in_place        : if True then replace the current time series
:return                : the detrended time series
:note                  : outliers from Gts.outliers are ommitted in the estimation and
offsets given Gts.offsets_dates are estimated simultaneously


### pyacs.gts.lib.model.detrend_seasonal(self, method='L2', in_place=False, periods=None, exclude_periods=None)
estimates a trend + annual + semi-annual terms in a time series and removes them
velocity, annual and semi-annual attributes are saved in Gts.velocity, Gts.annual, Gts.semi_annual

:param periods         : periods used for estimation
:param exclude_periods : periods to be excluded from estimation
:param in_place        : if True then replace the current time series
:return                : the detrended time series
:note                  : outliers from Gts.outliers are ommitted in the estimation and
offsets given Gts.offsets_dates are estimated simultaneously


### pyacs.gts.lib.model.remove_pole(self, pole, pole_type='euler', in_place=False, verbose=True)
remove velocity predicted by an Euler pole or a rotation rate vector from a time series
pole is a 1D array with 3 values
requires self.lon & self.lat attributes to have been filled before 
if in_place = True then replace the current time series


### pyacs.gts.lib.model.frame(self, frame=None, in_place=False, verbose=False)
Rotates a time series according to an Euler pole
Returns a new Gts instance


### pyacs.gts.lib.model.spline(self, smoothing=1, degree=5, date=None)

* **Parameters**

    **smoothing** – Positive smoothing factor used to choose the number of knots. Number of knots will be increased


until the smoothing condition is satisfied:

sum((w[i] \* (y[i]-spl(x[i])))\*\*2, axis=0) <= s


* **Parameters**

    
    * **degree** – Degree of the smoothing spline. Must be <= 5. Default is k=3, a cubic spline.


    * **date** – 1D array of interpolation dates in decimal year, or ‘day’ for every day. defualt None will interpolate


at data date only.
:return: new gts instance


### pyacs.gts.lib.model.smooth(self, window_len=11, window='hanning', in_place=False, verbose=False, component='NEU')
smooth a time series


### pyacs.gts.lib.model.make_model(self, option='detrend', method='L2', loutlier=None, in_place=False)
Estimate time series model parameters using least squares 
input: data: Gts format
option are: ‘detrend’/’detrend_annual’/’detrend_seasonal’
output: new Gts object: time series is now the residuals wrt to the model and its associated values (vel, annual, semi-annual etc)


### pyacs.gts.lib.model.mmodel(self)
Generates a modeled time series from the parameters read in self


### pyacs.gts.lib.model.detrend_median(self, delta_day=None, in_place=False, periods=[], exclude_periods=[], verbose=False, auto=False)
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



### pyacs.gts.lib.model.detrend_seasonal_median(self, wl=11, in_place=False, verbose=False)
Calculates a velocity using the median of pair of displacements exactly separated by one year, inspired from MIDAS and then removes repeating yearly signal
If the time series has less than three years of data, then the time series is kept untouched.
