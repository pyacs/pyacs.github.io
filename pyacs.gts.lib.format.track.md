---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.format.track
images: {}
path: /pyacs-gts-lib-format-track
title: pyacs.gts.lib.format.track module
---

# pyacs.gts.lib.format.track module

Reads GAMIT/GLOBK TRACK kinematics time series


### pyacs.gts.lib.format.track.read_track_NEU(self, tsdir='.', tsfile=None, leap_sec=0.0, eq_time=None, verbose=False)
Read a GAMIT/GLOBK Track output file generated with the option out_type NEU
in this case dates are seconds
by default the seconds are with respect to the first epoch of measurements
If option leap_sec is provided with a value > 0.0, then GPS time is corrected for the difference between GPTS time and UTC 
If eq_time is provided, it is assumed to be UTC. Expected format is YYYY:MM:MD:HH:MM:SS.S
