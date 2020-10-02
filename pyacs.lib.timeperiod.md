---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.timeperiod
images: {}
path: /pyacs-lib-timeperiod
title: pyacs.lib.timeperiod module
---

# pyacs.lib.timeperiod module


### exception pyacs.lib.timeperiod.TimePeriodUndefinedError()
Bases: `Exception`


### class pyacs.lib.timeperiod.TimePeriod(start_time=None, end_time=None)
Bases: `object`

The beginning of this period as datetime object


#### isdefined()

#### begin()

#### epoch_begin()

#### end()

#### epoch_end()

#### intersection(period)

#### has_in(date)
Tells whether a given date is in the period

return: True if the given date in within the period, False otherwise


#### display()

#### get_info()
