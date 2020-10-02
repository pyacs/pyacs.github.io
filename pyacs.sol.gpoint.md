---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.sol.gpoint
images: {}
path: /pyacs-sol-gpoint
title: pyacs.sol.gpoint module
---

# pyacs.sol.gpoint module


### class pyacs.sol.gpoint.Gpoint(X=None, Y=None, Z=None, SX=None, SY=None, SZ=None, epoch=None, code=None, pt=None, soln=None, domes=None, VX=None, VY=None, VZ=None, SVX=None, SVY=None, SVZ=None, Ve=None, Vn=None, Vu=None, SVe=None, SVn=None, SVu=None, lon=None, lat=None, he=None, Cv_xyz=None, Cv_enu=None, index=None)
Bases: `object`

Geodetic point

Used with sinex class


#### assign_index(index)

#### posxyz()

#### staxyz()

#### covarxyz()

#### covarenu()

#### velxyz()

#### read_from_sinex(sinex_name)
Reads an populate self from a sinex file


#### write_as_estimate(fname, index=1, VEL=True, VENU=None, CVENU=None, ENU=None, soln=1, epoch=2010.0)
Writes site information formatted for a ESTIMATE section of a sinex file


#### apply_helmert(T)

#### substract_pole(W=None, type='rot')
Substract the velocity predicted by an Euler pole or a rotation rate vector


#### xyz_distance(M)
