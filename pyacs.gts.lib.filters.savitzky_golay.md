---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.filters.savitzky_golay
images: {}
path: /pyacs-gts-lib-filters-savitzky-golay
title: pyacs.gts.lib.filters.savitzky_golay module
---

# pyacs.gts.lib.filters.savitzky_golay module

Savitzky-Golay filter for Gts based on scipy.signal.medfilt.
[http://https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html#scipy.signal.savgol_filter](http://https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html#scipy.signal.savgol_filter)
Additional information on Savitzky-Golay filter from [https://scipy-cookbook.readthedocs.io/items/SavitzkyGolay.html](https://scipy-cookbook.readthedocs.io/items/SavitzkyGolay.html)

The Savitzky Golay filter is a particular type of low-pass filter, well adapted for data smoothing. For further information see: [http://www.wire.tu-bs.de/OLDWEB/mameyer/cmr/savgol.pdf](http://www.wire.tu-bs.de/OLDWEB/mameyer/cmr/savgol.pdf) (or [http://www.dalkescientific.com/writings/NBN/data/savitzky_golay.py](http://www.dalkescientific.com/writings/NBN/data/savitzky_golay.py) for a pre-numpy implementation).

It has the advantage of preserving the original shape and
features of the signal better than other types of filtering
approaches, such as moving averages techniques.

The Savitzky-Golay is a type of low-pass filter, particularly
suited for smoothing noisy data. The main idea behind this
approach is to make for each point a least-square fit with a
polynomial of high order over a odd-sized window centered at
the point.


### pyacs.gts.lib.filters.savitzky_golay.savitzky_golay(self, in_place=False, verbose=True, window_length=15, polyorder=3, deriv=0, delta=1.0, mode='interp', cval=0.0)
returns a filtered time series using scipy.signal.savgol_filter

See documentation for the filter parameters.
[http://https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html#scipy.signal.savgol_filter](http://https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.savgol_filter.html#scipy.signal.savgol_filter)


* **Parameters**

    
    * **in_place** – if True then replace the current time series


    * **verbose** – boolean, verbose mode



* **Returns**

    the filtered time series
