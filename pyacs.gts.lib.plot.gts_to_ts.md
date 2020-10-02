---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.plot.gts_to_ts
images: {}
path: /pyacs-gts-lib-plot-gts-to-ts
title: pyacs.gts.lib.plot.gts_to_ts module
---

# pyacs.gts.lib.plot.gts_to_ts module


### pyacs.gts.lib.plot.gts_to_ts.gts_to_ts(gts, date=None, unit='mm', date_unit='decyear', date_ref=None, set_zero_at_date=None, center=True)
prepare a gts for plot.


* **Parameters**

    
    * **gts** – Gts instance


    * **date** – a list of dates [start_date , end_date] in decimal degrees. Default is None for all dates.


    * **unit** – unit for output


    * **date_unit** – date unit for the x-axis


    * **date_ref** – reference date in decimal year.


:return np_date, y, yerr
