---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.sinex.snxutils
images: {}
path: /pyacs-sinex-snxutils
title: pyacs.sinex.snxutils module
---

# pyacs.sinex.snxutils module


### pyacs.sinex.snxutils.earlier(t1, t2)

### pyacs.sinex.snxutils.read_domes(file, coord=True)

### pyacs.sinex.snxutils.read_solns(file)

### pyacs.sinex.snxutils.extract_solns(solns, snx, file, comment=None)

### pyacs.sinex.snxutils.helmert_outliers(code, pt, soln, v, vn, thr_raw=None, thr_norm=None, thr_auto=4.0, log=None, append=False)

### pyacs.sinex.snxutils.helmert14_outliers(code, pt, soln, v, vn, thr_raw=None, thr_norm=None, thr_auto=5.0, log=None, append=False)

### pyacs.sinex.snxutils.helmert_hist(v, unit='mm', nbins=100, output=None, no_up=False)

### pyacs.sinex.snxutils.helmert_map(lon, lat, v, unit='mm', h_scale=1, v_scale=1, legend=5, title=None, output=None, no_up=False)

### pyacs.sinex.snxutils.station_map(lon, lat, code, write_codes=True, title=None, output=None)

### pyacs.sinex.snxutils.meanpole(d, meanpm='IERS2010')

### pyacs.sinex.snxutils.read_opoleload(inp)

### pyacs.sinex.snxutils.compute_opoleload(opole, lon, lat, mjd, xpo, ypo, meanpm='IERS2010')

### pyacs.sinex.snxutils.compute_psd(snx, sta, t)
