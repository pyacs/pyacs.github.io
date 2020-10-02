---
date: '2020-10-02T17:56:24.758Z'
docname: foreword
images: {}
path: /foreword
title: What is pyacs?
---

# What is pyacs?

Pyacs is a framework (that is a set of tools and a way to think) to analyze and to model
geodetic data.

# The philosophy of pyacs

Although pyacs includes a few ready-to-use wrappers, pyacs is rather intended to provide
a set of tools for analysts that can be used to develop a specific application. pyacs is
constantly evolving, as new capabilities are added
depending on the need of users. pyacs comes as it is and no warranty.

Pyacs is not intending of replacing more complex softwares. Rather, pyacs enables quick
and robust solutions to be derived. Rapid solutions are achieved through neglecting the
full variance associated with solution. Robustness is ensure through extensive use of the
L1 norm. pyacs then provides inputs for running final solution in
particular in Glred/Globk.

# The components of pyacs

pyacs includes several components:


* **pyacs_lib:** a library of primitive functions for dates, coordinates, estimators, manipulation of geodetic results


* **interactive:** ipyacs.py launches the interactive environment, mainly for time series analysis


* **pyacs_sol:** includes the wrapper pyacs_make_time_series.py to produce time series


* **pyacsqgis:** conversion of gmt psvelo files to shapfile format to be readily visualized in QGIS


* **pyeq:** simple forward 2D elastic modeling, and scaling laws for earthquakes


* **pyeq_model:** 3D elastic models of co-,inter- and time dependent deformation (in development)


* **pygamit:** a few wrapper to help gamit processing


* **pygeca:** gamit processing in a cluster environment


* **pygts:** geodetic time series analysis


* **pygvel:** velocity field analysis
