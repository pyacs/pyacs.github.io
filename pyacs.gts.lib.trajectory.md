---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.trajectory
images: {}
path: /pyacs-gts-lib-trajectory
title: pyacs.gts.lib.trajectory module
---

# pyacs.gts.lib.trajectory module

Non linear trajectory models for Geodetic Time Series


### pyacs.gts.lib.trajectory.trajectory(self, model_type, offset_dates=[], eq_dates=[], H_fix={}, H_constraints={}, H_bounds={}, component='NEU', verbose=False)
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
