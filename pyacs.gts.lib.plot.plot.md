---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.plot.plot
images: {}
path: /pyacs-gts-lib-plot-plot
title: pyacs.gts.lib.plot.plot module
---

# pyacs.gts.lib.plot.plot module


### pyacs.gts.lib.plot.plot.plot(self, title=None, loffset=True, loutliers=True, verbose=False, date=[], yaxis=None, yupaxis=None, xticks_minor_locator=1, lcomponent=['N', 'E', 'U'], error_scale=1.0, lperiod=[[]], lvline=[], save_dir_plots='.', save=None, show=True, unit='mm', date_unit='decyear', date_ref=0.0, center=True, superimposed=None, lcolor=['r', 'g', 'c', 'm', 'y', 'k', 'b'], label=None, legend=False, set_zero_at_date=None, grid=True, plot_size=None, info=[], xlabel_fmt=None, \*\*kwargs)
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
