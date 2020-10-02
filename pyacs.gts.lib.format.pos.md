---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.format.pos
images: {}
path: /pyacs-gts-lib-format-pos
title: pyacs.gts.lib.format.pos module
---

# pyacs.gts.lib.format.pos module

Reads and write PBO pos files


### pyacs.gts.lib.format.pos.read_pos(self, tsdir='.', tsfile=None, xyz=True, verbose=False)
Read GAMIT/GLOBK PBO pos file in a directory and actually loads the time series


* **Parameters**

    
    * **tsdir** – directory of pos file


    * **tsfile** – pos file to be loaded


    * **xyz** – reads xyz sx sy sz corr_xy corr_xz corr_yz columns


    * **verbose** – verbose mode



* **Return Nothing**



* **Raises**

    **Nothing** – 



* **Note**

    Since a pos file includes (almost) all the information, data, code, X0,Y0,Z0,t0 will be populated


If file=None, then read_pos will look for a file named CODE\*.pos


### pyacs.gts.lib.format.pos.write_pos(self, idir, add_key='', force=None, verbose=False)
Write a time series in GAMIT/GLOBK PBO pos format


* **Parameters**

    
    * **idir** – output directory


    * **add_key** – if not blank then the output pos file will be CODE_add_key.pos, CODE.pos otherwise.


    * **force** – set force to ‘data’ or ‘data_xyz’ to force pos to be written from .data or .data_xyz



* **Note1**


default behaviour (force = None)
if data and data_xyz are not None, then print them independently
if there are data only, then uses X0,Y0,Z0 to write data_xyz
if there are data_xyz only, recreate data and write it
