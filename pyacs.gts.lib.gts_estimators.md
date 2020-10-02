---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.gts_estimators
images: {}
path: /pyacs-gts-lib-gts-estimators
title: pyacs.gts.lib.gts_estimators module
---

# pyacs.gts.lib.gts_estimators module


### pyacs.gts.lib.gts_estimators.least_square(A, L, P=None)
Least squares estimation for system equation AX + L = 0, P
input: A: design matrix;L observation vector L; P: weight matrix for L
(P defaut is the identity matrix)
output: unknown matrix  : X
residuals matrix: V
standard deviation sigma_0: std
unknown parameters variance: s_X
residuals variance: s_V
model S:S = A\*X
