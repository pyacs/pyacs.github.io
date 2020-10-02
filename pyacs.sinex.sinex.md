---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.sinex.sinex
images: {}
path: /pyacs-sinex-sinex
title: pyacs.sinex.sinex module
---

# pyacs.sinex.sinex module


### class pyacs.sinex.sinex.sinex()
Bases: `object`


#### classmethod read(file, dont_read=[])

#### write(file, dont_write=[], epochs_style='new')

#### check_staid(codomes, check_pt=True, check_crd=True, check_desc=True, log=None, append=False)

#### check_solns(solns, log=None, append=False)

#### check_erp()

#### get_xyz(code, pt=None, soln=None)

#### get_plh(code, pt=None, soln=None)

#### get_lonlat(code, pt=None, soln=None)

#### get_sigenh(code, pt, soln)

#### get_cov_sta(code, pt=None, soln=None)

#### get_helmert_matrix(params='RST', pole=False, gc=False)

#### map(write_codes=True, title=None, output=None)

#### propagate(epo, keep_vel=False)

#### remove_sta(code, pt=None, soln=None, log=None, append=False)

#### keep_sta(code, pt=None, soln=None, log=None, append=False)

#### remove_sta_wo_domes()

#### keep_relevant_solns(t, solns)

#### remove_params(types)

#### remove_undef_params()

#### unconstrain()

#### prior2ref(ref, log=None, append=False)

#### fix_params(types)

#### fix_sta(code, pt=None, soln=None, log=None, append=False)

#### reduce_params(types)

#### reduce_sta(code, pt=None, soln=None, log=None, append=False)

#### reduce_doublons(log=None, append=False)

#### setup_geocenter(tref)

#### setup_scale(tref)

#### reduce_helmerts(params)

#### add_min_const(params='', sigma=0.0001, code=None, pt=None, soln=None, reduce_B=False)

#### set_constraints(keep_const_on=[], add_const_on=[], add_const_sig=[], min_const_on='', min_const_sig=0.0001, code=None, pt=None, soln=None, reduce_B=False)

#### neqinv(keep_const_on=[], add_const_on=[], add_const_sig=[], min_const_on='', min_const_sig=0.0001, code=None, pt=None, soln=None, reduce_B=False)

#### rescale(f)

#### get_common_points(ref)

#### helmert_wrt(ref, params='RST', weighting='identity', with_vel=False, normalize=True, log=None, append=False)

#### trim_metadata(start, end)

#### update_stalist(sta, ac)

#### get_core(file, ref, thr=None, log=None, append=False)

#### extract_core(file, ref, thr=None, log=None, append=False)

#### apriori_sf(stdref)

#### add_metadata(metasnx, ref=None, comments=None, acks=None, t=None)

#### get_residuals(ref, erp=False, gc=False)

#### check_sat_pco(ref)

#### refsys_effect(params=['all'], log=None, append=False)

#### correct_opoleload(opole, mjd, meanpm='IERS2010', reverse=False)

#### get_nonpubsolns(sigmax, fcontr)

#### add_psd(psd)

#### remove_psd(psd)

#### add_per(file, T, tref)

#### plate_poles(file, Trate=True, weighting='full', log=None, append=False)

#### insert_disc(code, t)

#### apply_offsets(code, pt, soln, denh)

#### write_solndomes(solns, file)

#### loadest_wrt(ref, center, lmax, lovefile, weighting='full', log=None, append=False)
