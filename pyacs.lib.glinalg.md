---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.glinalg
images: {}
path: /pyacs-lib-glinalg
title: pyacs.lib.glinalg module
---

# pyacs.lib.glinalg module

Linear algebra for Geodesy problems


### pyacs.lib.glinalg.ls(G, d, verbose=False)
Solve the least-squares (LS) problem m so that  

```
|
```

Gx-d|\*\*2 is minimum.


* **Parameters**

    
    * **G** – m x n model matrix as 2D numpy array


    * **d** – m 1D numpy observation vector


    * **verbose** – verbose mode



* **Returns**

    x,chi2: m (1D numpy array of dim m), chi2 (chi-square)



* **Note**

    solved through numpy.linalg.lstsq



### pyacs.lib.glinalg.lsw(G, d, std)
Solve the least-squares (LS) with data uncertainties provided as a vector


* **Parameters**

    
    * **G** – m x n model matrix as 2D numpy array


    * **d** – m 1D numpy observation vector


    * **std** – standard deviation vector for d



* **Note**

    the system is modified to be solved by ordinary LS by the change G<- (G.T/std).T and d<- d/std



### pyacs.lib.glinalg.lscov(G, d, cov, method='chol')
Solve the least-squares (LS) problem with data covariance


* **Parameters**

    
    * **G** – m x n model matrix as 2D numpy array


    * **d** – m 1D numpy observation vector


    * **cov** – covariance matrix for d



### pyacs.lib.glinalg.lsw_full(G, d, std, verbose=False)
Solve the least-squares (LS) with data uncertainties provided as a vector and returns the posterior covariance


* **Parameters**

    
    * **G** – m x n model matrix as 2D numpy array


    * **d** – m 1D numpy observation vector


    * **std** – standard deviation vector for d



### pyacs.lib.glinalg.lscov_full(G, d, cov, verbose=False)
Solve the least-squares (LS) with data covariance and returns the posterior covariance


* **Parameters**

    
    * **G** – m x n model matrix as 2D numpy array


    * **d** – m 1D numpy observation vector


    * **cov** – covariance matrix for d



### pyacs.lib.glinalg.cov_to_invcov(M)
Inverse a covariance matrix


* **Parameters**

    **cov** – 2D numpy array covariance matrix



* **Returns**

    2D numpy array inverse covariance matrix



### pyacs.lib.glinalg.corr_to_cov(corr, sigma_m)
Correlation to covariance matrix


* **Parameters**

    
    * **corr** – correlation matrix


    * **sigma_m** – vector of standard deviation = sqrt(diag(Cov))


:return covariance matrix


### pyacs.lib.glinalg.cov_to_corr(Cov)
Covariance to correlation transformation


* **Parameters**

    **cov** – covariance matrix



* **Return corr,sigma_m**

    correlation matrix and standard deviation matrix



### pyacs.lib.glinalg.symmetrize(a, type_matrix)
Extract the upper or lower triangle and make a symmetric matrix


* **Parameters**

    
    * **a** – numpy 2D array, must be a square matrix


    * **type** – ‘triu’ or ‘tril’, triangle used to form the matrix



### pyacs.lib.glinalg.dot_and_sum(LX, a)
does a matrix by scalar product and sum it
:param LX : list of arrays with the same dimension
:param a  : list of scalars


### pyacs.lib.glinalg.repeat_matrix_in_col(G, n)
Repeat a matrix along a column

R = np.empty( ( n,G.shape[0], G.shape[1] ) )
R[:] = G
return( R.reshape( n\*G.shape[0], G.shape[1])  )


### pyacs.lib.glinalg.odot(a, G)
> Customize vector by matrix product.

> Let’s assume we have a matrix made of equal dimension sub-matrices $G_1,cdots, G_n$
> egin{equation}
> left[
> egin{array}{c}
> G_1G_2

dots 

    G_n
    end{array}

ight]

    end{equation}
    and a vector of scalars
    egin{equation}
    left[
    egin{array}{c}
    a_1a_2

dots 

    a_n
    end{array}

ight]

    end{equation}
    and we want
    egin{equation}
    left[
    egin{array}{c}
    a_1 G_1a_2 G_2

dots 

    a_n G_n
    end{array}

ight]

    end{equation}
    We do this with numpy broadcasting


    * **param a**

        1D numpy array of multipliers (scalars)



    * **param G**

        2-D numpy arrays of submatrix G_i.



    * **return**

        result of the multiplication



    * **note**

        if G.shape = (n,m), and a.shape=(l), then the shape of the G_i is (n/l,m)



### pyacs.lib.glinalg.dot(A, B)
Matrix/matrix, matrix/vector and vector/vector multiplication
:author  : P. Rebischung
:date:Created : 02-Aug-2013
:changes :
:param A: Matrix or vector
:param B : Matrix or vector
:return:  A\*B


### pyacs.lib.glinalg.syminv(M)
Invert a symmetric matrix
:author  : P. Rebischung
:created : 02-Aug-2013
:param M : Matrix
:return:Inverse matrix


### pyacs.lib.glinalg.sympinv(M, verbose=False)
Pseudo-invert a positive semi-definite symmetric matrix
:author: P. Rebischung
:created : 02-Aug-2013
:param M : Matrix
:return: Pseudo-inverse


### pyacs.lib.glinalg.make_normal_system(A, d, inv_Cd)
Given the linear system A x = d with Cd the covariance matrix of d
the associated normal system is A.T Cd-1 A x = A.T Cd-1 d.
returns N= A.T Cd-1 A, Nd=A.T Cd-1 d


### pyacs.lib.glinalg.make_normal_system_tarantola(G, d, m0, inv_Cd, inv_Cm)
returns Gt inv_Cd G + inv_Cm , Gt inv_Cd d + inv_Cm m0


### pyacs.lib.glinalg.matrix_from_pattern(pattern, structure)
creates a matrix made of a pattern according to a structure

:param pattern : pattern 2D numpy array to be duplicated
:param structure: 2D numpy array giving the structure as multiplicating factors
:return: the block matrix as a 2D numpy array

```python
>>> pattern = np.arange(6).reshape(2,3)
>>> structure = np.arange(6).reshape(3,2)
```

```python
>>> print(pattern)
>>> print('--')
>>> print(structure)
>>> print('--')
>>> print( matrix_from_pattern( pattern , structure ) )
```

> [[0 1 2]
> [3 4 5]]
> –
> [[0 1]

> > [2 3]
> > [4 5]]

> –
> [[ 0  0  0  0  1  2]

> > [ 0  0  0  3  4  5]
> > [ 0  2  4  0  3  6]
> > [ 6  8 10  9 12 15]
> > [ 0  4  8  0  5 10]
> > [12 16 20 15 20 25]]


### pyacs.lib.glinalg.extract_block_diag(a, n, k=0)
