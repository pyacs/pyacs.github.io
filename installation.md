---
date: '2020-10-02T17:56:24.758Z'
docname: installation
images: {}
path: /installation
title: How to install pyacs?
---

# How to install pyacs?

## Requirements

pyacs is written in python. Since 2018, pyacs has moved to python 3.6. makes an intensive use of the following python libraries:


* Numpy


* Scipy


* Matplotlib


* ipython

I recommend to use a Scientific Python Package like Anaconda or Enthought, which
comes with all libraries installed. Anaconda 2.4.1 was used for pyacs development.

pyacs includes in its distribution the following packages:


* euclide


* argparse


* GpsTime

These two packages are distributed with pyacs to keep a single, stable version compatible
with the code.

The software R

Some additional softwares like QGIS and the plugin ArrowRenderer are useful to visualize
results.

Finally, use of the elastic models libraries requires additional program:


* edgrn/edcmp

## Installation

Installation should be straightforward if you have Anaconda installed. For a tar bz2 ball pyacs.X.tar.bz2, just type

```
pip install pyacs.X.tar.bz2
```

Anaconda pip program should install all required packages first and then install pyacs components.

You can uninstall pyacs any time by typing

```
pip uninstall pyacs
```

## Setting your environment


* First, check that env python properly launches python 2.7.x


* Check that env ipython properly launches ipython


* verify that Numpy, Scipy and Matplotlib can properly be imported

In your *.bashrc* or *.bash_profile*, or *.cshrc* depending on your environment , add (example for a bash environment)

```
# PYACS ALIAS
alias ipyacs='ipython `which ipyacs.py` -i'
```

Once done, source you configuration file, or open a new terminal window. Check pyacs is working

```
ipyacs
```

should return something like

```
-- Welcome to pyacs interactive environment -- version  0.02
- Importing pyacs core module
- Importing pyacs.gts module
- Importing numpy as np
- Importing matplotlib.pyplot as plt
- Trying to read time series files
-- Reading directory:  .
-- No mb_files found
-- Importing modules Velocity_Field, Gpoint  ./../stat/pyacs_void.gmt
```

In [1]:

try to import pyacs

```
import pyacs
```
