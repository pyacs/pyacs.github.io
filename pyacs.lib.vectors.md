---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.vectors
images: {}
path: /pyacs-lib-vectors
title: pyacs.lib.vectors module
---

# pyacs.lib.vectors module

Useful operations on vectors (1-D numpy array)


### pyacs.lib.vectors.np_array(X)
Converts to 1-D numpy array


* **Parameters**

    **X** – list or tuple to be converted


:return : 1D numpy array


### pyacs.lib.vectors.norm(X)
Returns the norm of a vector


* **Parameters**

    **X** – list, tuple or 1D numpy array


:return : norm (float)


### pyacs.lib.vectors.normalize(X)
Normalize a vector


* **Parameters**

    **X** – list, tuple or 1D numpy array


:return : 1D numpy array


### pyacs.lib.vectors.scal_prod(X, Y)
Returns the scalar products


* **Parameters**

    **X****,****Y** – list, tuple or 1D numpy array


:return : scalar product as float


### pyacs.lib.vectors.vector_product(A, B)
Vector product

> A[1]\*B[2] - B[1]\*A[2]

vector_product(A,B)=  A[2]\*B[0] - B[2]\*A[0]

    A[0]\*B[1] - B[0]\*A[1]


* **Parameters**

    **A****,****B** – 1D numpy arrays



* **Return AxB**

    1D numpy array
