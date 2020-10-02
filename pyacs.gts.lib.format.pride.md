---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.format.pride
images: {}
path: /pyacs-gts-lib-format-pride
title: pyacs.gts.lib.format.pride module
---

# pyacs.gts.lib.format.pride module

Reads PRIDE kinematic files


### pyacs.gts.lib.format.pride.read_pride(self, tsdir='.', tsfile=None, xyz=True, verbose=False)
Read PRIDE-PPPAR kinematic result file


* **Parameters**

    
    * **tsdir** – directory of pride-pppar kinematic files


    * **tsfile** – pride-pppar kinematic file to be loaded


    * **verbose** – verbose mode



* **Return Nothing**



* **Raises**

    **Nothing** – 


If file=None, then read_pride will look for a files named kin_\*code


### pyacs.gts.lib.format.pride.read_pride_pos(self, tsdir='.', tsfile=None, verbose=False)
Read PRIDE-PPPAR static result file


* **Parameters**

    
    * **tsdir** – directory of pride-pppar pos static files


    * **tsfile** – pride-pppar pos static file to be loaded


    * **verbose** – verbose mode


If file=None, then read_pride will look for a files named pos_\*code
