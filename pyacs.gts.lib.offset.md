---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.offset
images: {}
path: /pyacs-gts-lib-offset
title: pyacs.gts.lib.offset module
---

# pyacs.gts.lib.offset module


### pyacs.gts.lib.offset.print_no_return(str)

### pyacs.gts.lib.offset.suspect_offsets_mf(self, threshold=3, verbose=True, lcomponent='NE', n_max_offsets=5, in_place=False, debug=False)
Tries to find offsets in a time series using a median filter


### pyacs.gts.lib.offset.test_offset_significance(self, date, conf_level=95, lcomponent='NE', verbose=True, debug=False, mode='local')
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



### pyacs.gts.lib.offset.local_offset_robust(self, date, n, verbose=False, debug=False)
estimate a local offset (no velocity) with a robust method


* **Parameters**

    
    * **date** – date in decimal year


    * **n** – number of dates before and after the dates used in the estimation


:return : a 1D numpy array with [date, north, east, up, s_north, s_east, s_up]


* **Note**

    the offsets are estimated using the difference between the median position before and after the earthquake using i days


for all i <=n. Then the median of the estimates is returned.


### pyacs.gts.lib.offset.apply_offsets(self, np_offset, opposite=False, in_place=False, verbose=False)
Applies given offsets to a times series
np_offset is a 1D np.array with lines [dates,north,east,up]
if in_place = True then replace the current time series


* **Parameters**

    
    * **np_offset** – 1D or 3D numpy array or list or list of list with column offset_dates, north, east, up, s_north, s_east, s_up


    * **opposite** – boolean, if True apply the oppsite of provided offsets


    * **in_place** – if True, will make change in place, if False, return s a new time series


    * **verbose** – boolean, verbose mode



### pyacs.gts.lib.offset.find_offsets_t_scan(self, threshold=0.8, window=250, in_place=False, lcomponent='NE', verbose=True, debug=True)

### pyacs.gts.lib.offset.get_suspected_dates(diff_data, threshold, lcomponent='NEU', verbose=False)
get the list of the largest values; these are suspected offsets


### pyacs.gts.lib.offset.check_suspected_offsets(lindex, verbose=False)
Check that the list of suspected index does not contain two successive values.
In this case, it is certainly an isolated outlier and the suspected offsets are removed from the list.


### pyacs.gts.lib.offset.find_offsets(self, threshold=3, n_max_offsets=9, conf_level=95, lcomponent='NE', verbose=True, in_place=False)
A simple empirical procedure to find offsets.


* **Parameters**

    
    * **threshold** – threshold value for offset preliminary detection


    * **n_max_offset** – maximum number of offsets to be detected simultaneously


    * **conf_level** – confidence level for a suspected offset to be accepted


    * **lcomponent** – components used for offset detection



* **Returns**

    a new Gts instance with offsets_dates and outliers now populated



### pyacs.gts.lib.offset.suspect_offsets(self, threshold=3, verbose=True, lcomponent='NE', n_max_offsets=10, in_place=False)
Tries to find offsets in a time series


### pyacs.gts.lib.offset.find_time_offsets(self, option=None, ndays=7, th_detection_rms=3, th_detection_offset=3)
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


### pyacs.gts.lib.offset.delete_small_offsets(self, offsets, del_by_pricise=False)
The aim for test_offset modul. 
Estimate the offsets with clean data.
Then delete the offsets which their values are so small
input: list of time offsets
output: list of time offsets tested


### pyacs.gts.lib.offset.test_offsets(self, verbose=False, debug=True, window_length=None)
Test the offset:

    
    * delete the small offset (1mm for East/North, 2mm for Up)


    * then make a F ratio test


    * re-check to delete the small offsets


### pyacs.gts.lib.offset.estimate_local_offset(self, window_length=4, in_place=False)
Estimate the local offset, just used window_length positions before & window_length positions behind of offset
output: amplitude of local offsets
