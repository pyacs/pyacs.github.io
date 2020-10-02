---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.Sgts_methods.read_ts
images: {}
path: /pyacs-gts-sgts-methods-read-ts
title: pyacs.gts.Sgts_methods.read_ts module
---

# pyacs.gts.Sgts_methods.read_ts module


### pyacs.gts.Sgts_methods.read_ts.read_ts(self, ts_dir='.', verbose=True, name_filter='', add_key='', sites=[], lexclude=[], type=None, xyz=True)
Reads time series, trying to guess the format. Current time series format supported are: pos, kenv, mb_file, cats, txyz (pyacs), track (NEU format for high rate)


* **Parameters**

    
    * **ts_dir** – directory of time series files


    * **name_filter** – string used to filter time series name ‘*name_filter*’


    * **add_key** – adds a string before site code


    * **sites** – list of site codes to be read. Any other will be discarded.


    * **lexclude** – list of sites to be excluded from reading


    * **type** – specifies the format of the time series files. Choose among [‘pos’, ‘kenv’, ‘mb_file’, ‘cats’, ‘txyz’, ‘track’ , ‘pride’,’pck’]


    * **xyz** – for pos files, reads the XYZ coordinates rather than dNEU. This is the default.



* **Returns**

    an Sgts instance.
