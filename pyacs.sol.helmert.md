---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.sol.helmert
images: {}
path: /pyacs-sol-helmert
title: pyacs.sol.helmert module
---

# pyacs.sol.helmert module

calculates Helmert transformation


### pyacs.sol.helmert.helmert_matrix(x, y, z, tran=True, rot=True, scale=True, equilibrate=True)
Generates a Helmert transformation matrix for a single point
Can also create translation/rotation/scale transformation matrix


* **Parameters**

    
    * **x****,****y****,****z** – point geocentric coordinates (m)


    * **tran****,****rot****,****scale** – boolean telling that translation/rotation/scale will be included


    * **equilibrate** – (default True) changes the unit of the matrix so that x are in km and scale in mas for better conditionning of the matrix



* **Returns H**

    the transformation matrix as 2D numpy matrix



### pyacs.sol.helmert.observation_equation_helmert_local(xf, yf, zf, xr, yr, zr, tran=True, rot=True, scale=True)
Generate the linear transformation equation system for coordinate of a sites in two reference system.
The equation system is generated for E,N,U components


* **Parameters**

    
    * **xf****,****yf****,****zf** – geocentric coordinates in the initial reference (also called ‘free’ frame)


    * **xr****,****yr****,****zr** – geocentric coordinates in the final reference (the reference frame)


    * **tran****,****rot****,****scale** – boolean telling that translation/rotation/scale will be included



* **Return A,B**

    the design matrix and observation vector



* **Note**

    VCV not accounted yet



### pyacs.sol.helmert.estimate_helmert(H_Gpoint_ref, H_Gpoint_free, vcv_xyz=None, psd=None, tran=True, rot=True, scale=True, lexclude=[], method='Dikin_LS', threshold=5.0, verbose=True)
Estimates Helmert or transformation parameters between two sets of coordinates
Default is a 7-parameters transformation (translation, rotation & scale)

:param H_Gpoint_ref : dictionary of Geodetic Points (Gpoint instance) used as reference
:param H_Gpoint_free: dictionary of Geodetic Points (Gpoint instance) used as free
:param psd: psd object from sinex library for post-seismic deformation
:param tran,rot,scale: boolean telling if the transformation will use translation/rotation/scale 
:param method: ‘LS’ (Least-Squares) or ‘Dikin_LS’ (a sequence of L1 and L2 norm) estimation
:param threshold: threshold value for outlier rejection (default 5.)
:param verbose: boolean


### pyacs.sol.helmert.find_outliers_Helmert(R, threshold=5)
Returns index outliers points
