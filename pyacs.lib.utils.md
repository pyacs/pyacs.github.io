---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.utils
images: {}
path: /pyacs-lib-utils
title: pyacs.lib.utils module
---

# pyacs.lib.utils module

Various useful routines


### pyacs.lib.utils.numpy_array_2_numpy_recarray(A, names)
Converts a numpy array to a numpy recarray
names is the names of each field


### pyacs.lib.utils.numpy_recarray_2_numpy_array(A)
Converts a structured array (with homogeneous dtype) to a np.array


### pyacs.lib.utils.save_np_array_with_string(A, S, fmt, outfile, comment='')
saves a numpy array as a text file.
This is equivalent to np.savetxt except that S contains strings that are added to each row.


* **Parameters**

    
    * **A** – 2D numpy array to be saved


    * **S** – 1D numpy string array. S.ndim = A.shape[0]


    * **fmt** – format for printing


    * **outfile** – out file



* **Example**


A = np.arange(4).reshape(-1,2)
S = np.array([‘lima’,’quito’])
from pyacs.lib.utils import save_np_array_with_string
save_np_array_with_string(A,S,”%03d %03d %s”,’test.dat’)


### pyacs.lib.utils.make_grid(outfile, min_lon, max_lon, min_lat, max_lat, nx=None, ny=None, step_x=None, step_y=None, format='psvelo', comment='')
Generates a text file as a grid


* **Parameters**

    
    * **outfile** – output file name


    * **min_lon****,****max_lon****,****min_lat****,****max_lat** – grid bounds coordinates in decimal degrees


    * **ny** (*nx*) – number of points in the grid along longitude. If ny is not provided, ny=nx


    * **step_x****,****step_y** – step for the grid. This is an alternative to nx. If step_y is not provided, step_y=step_x


    * **format** – if format is None, then only lon, lat are written. If format=’psvelo’ (default), then the line is filled with 0. and sequentially site names


    * **comment** – comment to be added to the output file.



* **Returns**

    the grid as 2D numpy array



### pyacs.lib.utils.str2list_float(my_str)
Converts a list provided as a string to a true list of float


* **Parameters**

    **my_str** – string e.g. ‘[0,2.5,1E9]’


:return:[0,2.5,1E9]
