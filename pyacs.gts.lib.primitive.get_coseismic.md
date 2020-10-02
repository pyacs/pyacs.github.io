---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.get_coseismic
images: {}
path: /pyacs-gts-lib-primitive-get-coseismic
title: pyacs.gts.lib.primitive.get_coseismic module
---

# pyacs.gts.lib.primitive.get_coseismic module


### pyacs.gts.lib.primitive.get_coseismic.get_coseismic(self, eq_date, window_days=5, sample_after=1, method='median', in_place=False)
Get coseismic displacement at a given date.
Coseismic displacement is estimated as the position difference between the median of window_days before 
the earthquake date and the median of sample_after samples after the earthquake date.

note: only median method implemented
