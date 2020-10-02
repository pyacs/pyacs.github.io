---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.Sgts_methods.read_gts_conf
images: {}
path: /pyacs-gts-sgts-methods-read-gts-conf
title: pyacs.gts.Sgts_methods.read_gts_conf module
---

# pyacs.gts.Sgts_methods.read_gts_conf module


### pyacs.gts.Sgts_methods.read_gts_conf.read_gts_conf(self, gts_conf_file, verbose=False)
Reads a gts_conf_file
implemented commands in the file are:
#todo add_break      [site]  [date] # date is either [decyear] [doy year] [mday month year]
apply_offset   [site]  [offset_north,offset_east,offset_up] [date] # offset  applied is in mm, date is either [decyear] [doy year] [mday month year]
remove_offset   [site]  [offset_north,offset_east,offset_up] [date] # offset removed is in mm, date is either [decyear] [doy year] [mday month year]
#todo extract_periods [site] [date1,date2] # date is either [decyear] [doy year] [mday month year]
#todo exclude_periods [site] [date1,date2] # date is either [decyear] [doy year] [mday month year]
#todo remove_day    [site] [date]
