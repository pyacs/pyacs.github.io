---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.format.cats
images: {}
path: /pyacs-gts-lib-format-cats
title: pyacs.gts.lib.format.cats module
---

# pyacs.gts.lib.format.cats module

Reads and writes time series files in the CATS format


### pyacs.gts.lib.format.cats.read_cats_file(self, idir='.', ifile=None, gmt=True, verbose=False)
Read cats files in a directory and actually loads the time series


### pyacs.gts.lib.format.cats.write_cats(self, idir, offsets_dates=None, add_key='')
Writes a file for a cats analysis
if offsets_dates is not None then offsets are added at the beginning of the file
