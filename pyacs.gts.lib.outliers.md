---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.outliers
images: {}
path: /pyacs-gts-lib-outliers
title: pyacs.gts.lib.outliers module
---

# pyacs.gts.lib.outliers module


### pyacs.gts.lib.outliers.remove_outliers(self, periods=None, in_place=False)
removes outliers provided in self.outliers
return a new Gts without the outliers
if in_place = True then self has the outliers removed as well (in _place)


### pyacs.gts.lib.outliers.find_outlier_around_date(self, date, conf_level=95, n=3, lcomponent='NE', verbose=True)
Find an outlier around a given date 
returns the index of the outlier, returns [] if no outlier found
:param date       : given date
:param conf_level : confidence level for F_ratio test of outlier significance (default 95%%)
:param n          : number of dates either sides of date (default n=3)
:param lcomponent : components ‘N’,’E’,’U’,’NE’,’NEU’ (default ‘NE’)


### pyacs.gts.lib.outliers.find_outliers_percentage(self, percentage=0.03, in_place=False, verbose=False, component='NEU', periods=None, excluded_periods=None)
detrend a time series and
ranks the residuals by increasing absolute value
populate the outliers with the x % largest ones on each component


### pyacs.gts.lib.outliers.find_outliers_simple(self, threshold=100, window_length=10, in_place=False, verbose=False, component='NEU', periods=None, excluded_periods=None)

### pyacs.gts.lib.outliers.find_outliers_and_offsets_through_differentiation(self, th=100)
find outliers and offsets using differenciation


### pyacs.gts.lib.outliers.find_outliers_by_RMS_ts(self, ndays=7, th_detection=5, th_rejection=2)
Find index of outliers in a time series, populate self.outliers.

    
    * rms time series are first calculated over ndays


    * time windows are kept for further inspection if rms(t) > th_detection \* median(rms(ts))


    * for each anomalous time windows, differentiate positions, find the max


    * test whether it is a true outlier (differentiated(t) > th_rejection \* median(differentiated))

output:

    None


### pyacs.gts.lib.outliers.find_outliers_by_residuals(self, threshold=5, model='detrend_seasonal', component='NE', in_place=False)
Find index of outliers by trendline/trendline_annual/trendline_seasonal (the complete model)
Then the outliers are detected if their residuals are greater than th_rejection\*standard_deviation

output:

    Add the list of outlier index into self.outliers


### pyacs.gts.lib.outliers.find_outliers_vondrak(self, threshold=10, fc=2.0, in_place=False, verbose=True, periods=[[]], excluded_periods=[[]], component='NE')
Find outliers using a Vondrak filter


### pyacs.gts.lib.outliers.find_outliers_sliding_window(self, threshold=3, in_place=False, verbose=True, periods=[[]], excluded_periods=[[]], component='NE', window_len=15, automatic=True)
Find outliers using sliding windows
