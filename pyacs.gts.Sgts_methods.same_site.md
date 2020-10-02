---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.Sgts_methods.same_site
images: {}
path: /pyacs-gts-sgts-methods-same-site
title: pyacs.gts.Sgts_methods.same_site module
---

# pyacs.gts.Sgts_methods.same_site module


### pyacs.gts.Sgts_methods.same_site.same_site(self, dc=10, in_place=True, verbose=False)
Check that all gts in the current Sgts are actually the same site. If a given time series is
found to be of two separate sites, then a new gts is added to the return Sgts instance.

param dc: critical distance to decide to split the time series
param in_place: if True modify current Sgts, False retuen a new Sgts
param verbose: verbose mode

return: a new Sgts instance
