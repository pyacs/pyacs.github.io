---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.gts.lib.primitive.insert_gts_data
images: {}
path: /pyacs-gts-lib-primitive-insert-gts-data
title: pyacs.gts.lib.primitive.insert_gts_data module
---

# pyacs.gts.lib.primitive.insert_gts_data module


### pyacs.gts.lib.primitive.insert_gts_data.insert_gts_data(self, gts, in_place=False, verbose=False)
insert data (and/or) .data_xyz of a gts into the current gts


* **Parameters**

    
    * **gts** – tie series to be inserted


    * **in_place** – boolean, if True add_obs to the current Gts, if False, returns a new Gts


    * **verbose** – verbose mode


:return : new Gts or the modified Gts if in_place
