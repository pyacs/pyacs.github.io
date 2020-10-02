---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.Sgts_methods.medvel
images: {}
path: /pyacs-gts-sgts-methods-medvel
title: pyacs.gts.Sgts_methods.medvel module
---

# pyacs.gts.Sgts_methods.medvel module


### pyacs.gts.Sgts_methods.medvel.medvel(self, outdir=None, verbose=False)
Automatic velocity estimates using median estimator.
The code is adapted from the MIDAS approach (Blewitt et al., 2016).

medvel fills the velocity attribute of every Gts from the current Sgts instance.

returns the modified Sgts instance
Optionally, if outdir option is provided, writes the results in outdir


* **Param**

    outdir: output directory, default None



* **Param**

    verbose: boolean, verbose mode



* **Param**

    warning: output warning file



* **Reference**

    Blewitt, G., Kreemer, C., Hammond, W. C., & Gazeaux, J. (2016). MIDAS robust trend estimator for accurate GPS station velocities without step detection. Journal of Geophysical Research: Solid Earth, 121(3), 2054-2068.
