---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.remove_velocity
images: {}
path: /pyacs-gts-lib-primitive-remove-velocity
title: pyacs.gts.lib.primitive.remove_velocity module
---

# pyacs.gts.lib.primitive.remove_velocity module


### pyacs.gts.lib.primitive.remove_velocity.remove_velocity(self, vel_neu, in_place=False)
remove velocity from a time series
vel_neu is a 1D array of any arbitrary length, but with the velocities (NEU) to be removed in the first 3 columns
if in_place = True then replace the current time series
