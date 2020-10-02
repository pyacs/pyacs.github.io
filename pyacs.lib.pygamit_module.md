---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.pygamit_module
images: {}
path: /pyacs-lib-pygamit-module
title: pyacs.lib.pygamit_module module
---

# pyacs.lib.pygamit_module module

module for Gamit


### pyacs.lib.pygamit_module.read_qfile(qfile)
Reads a qfile and returns the following information:
- number of sites included in the analysis
- list of sites that do not have solution
- list of sites with large adjustment
- total number of ambiguities
- total number of fixed ambiguities
- the pre/postfit values
- Normal end in solve


### pyacs.lib.pygamit_module.get_nearest_from_apr(aprfile, n, linclude, lexclude, X, Y, Z, dec_year)
Returns the n nearest site from X,Y,Z present in linclude and apr


### pyacs.lib.pygamit_module.substitute_site(aprfile, site, X, Y, Z, dec_year)
Substitute an entry in apr file


### pyacs.lib.pygamit_module.update_apr(input_apr, target_apr, threshold, action)
Update an apr file using another apr
threshold is a minimum value for updating
if action is False only check


### pyacs.lib.pygamit_module.make_apr_doy(input_apr, output_apr, lsite, doy, year)
Creates an apr file for a given list of sites and select the best coordinates according to dates
