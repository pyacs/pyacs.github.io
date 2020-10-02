---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.step_detect
images: {}
path: /pyacs-gts-lib-step-detect
title: pyacs.gts.lib.step_detect module
---

# pyacs.gts.lib.step_detect module

Thomas Kahn
[thomas.b.kahn@gmail.com](mailto:thomas.b.kahn@gmail.com)


### pyacs.gts.lib.step_detect.t_scan(L, window=1000.0, num_workers=- 1)
Computes t statistic for i to i+window points versus i-window to i
points for each point i in input array. Uses multiple processes to
do this calculation asynchronously. Array is decomposed into window
number of frames, each consisting of points spaced at window
intervals. This optimizes the calculation, as the drone function
need only compute the mean and variance for each set once.
Parameters
———-
L : numpy array

> 1 dimensional array that represents time series of datapoints

window

    Number of points that comprise the windows of data that are
    compared

num_workers

    Number of worker processes for multithreaded t_stat computation
    Defult value uses num_cpu - 1 workers

t_stat

    Array which holds t statistic values for each point. The first 
    and last (window) points are replaced with zero, since the t
    statistic calculation cannot be performed in that case.


### pyacs.gts.lib.step_detect.mz_fwt(x, n=2)
Computes the multiscale product of the Mallat-Zhong discrete forward
wavelet transform up to and including scale n for the input data x.
If n is even, the spikes in the signal will be positive. If n is odd
the spikes will match the polarity of the step (positive for steps
up, negative for steps down).
This function is essentially a direct translation of the MATLAB code
provided by Sadler and Swami in section A.4 of the following:
[http://www.dtic.mil/dtic/tr/fulltext/u2/a351960.pdf](http://www.dtic.mil/dtic/tr/fulltext/u2/a351960.pdf)
Parameters
———-
x : numpy array

> 1 dimensional array that represents time series of data points

n

    Highest scale to multiply to

prod

    The multiscale product for x


### pyacs.gts.lib.step_detect.find_steps(array, threshold)
Finds local maxima by segmenting array based on positions at which
the threshold value is crossed. Note that this thresholding is 
applied after the absolute value of the array is taken. Thus,
the distinction between upward and downward steps is lost. However,
get_step_sizes can be used to determine directionality after the
fact.
Parameters
———-
array : numpy array

> 1 dimensional array that represents time series of data points

threshold

    Threshold value that defines a step

steps

    List of indices of the detected steps


### pyacs.gts.lib.step_detect.get_step_sizes(array, indices, window=1000)
Calculates step size for each index within the supplied list. Step
size is determined by averaging over a range of points (specified
by the window parameter) before and after the index of step
occurrence. The directionality of the step is reflected by the sign
of the step size (i.e. a positive value indicates an upward step,
and a negative value indicates a downward step). The combined 
standard deviation of both measurements (as a measure of uncertainty
in step calculation) is also provided.
Parameters
———-
array : numpy array

> 1 dimensional array that represents time series of data points

indices

    List of indices of the detected steps (as provided by 
    find_steps, for example)

window

    Number of points to average over to determine baseline levels
    before and after step.

step_sizes

    List of the calculated sizes of each step

step_error : list
