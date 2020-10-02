---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.Sgts_methods.read_gmt
images: {}
path: /pyacs-gts-sgts-methods-read-gmt
title: pyacs.gts.Sgts_methods.read_gmt module
---

# pyacs.gts.Sgts_methods.read_gmt module


### pyacs.gts.Sgts_methods.read_gmt.read_gmt(self, gmt=True, verbose=False, vel=False)
Reads a gmt psvelo file and populates lon and lat attributes for each Gts of Sgts


* **Parameters**

    
    * **gmt** – if True tries to read ‘/../stat/pyacs_void.gmt’, if a string then it is the gmt file to be read.


    * **verbose** – verbose mode


    * **vel** – boolean. If True, fills the .velocity attribute of every time series with the values read in the gmt file.



* **Note**

    this method is always in place.
