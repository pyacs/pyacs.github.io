---
date: '2020-10-02T17:56:24.758Z'
docname: tutorial_cluster_processing
images: {}
path: /tutorial-cluster-processing
title: 'pygeca: GNSS cluster processing with GAMIT'
---

# pygeca: GNSS cluster processing with GAMIT

pygeca stands for pyacs-gamit-en-cluster-a-geoazur.
pygeca is the part of pyacs that allows you to process large GNSS networks in a cluster computing environment using the OAR scheduler.
All commands starts with 

```
pygeca_
```

.

## Making job command files

job command files are text files including a list of commands interpreted by OAR to send processing to available nodes.
A typical job files looks like this:

```
#!/bin/bash
. /user/nocquet/.bashrc
#OAR -l core=1,walltime=60:00:0
#OAR -n soam_001_2018
#OAR -O %jobid%.out
#OAR -p ib='none' OR ib='DDR' OR ib='QDR'
cd /tmp
pygeca_subnetworks.py  --dir_conf /projet/gps/geodesy/process/soam_setup --sd 001 --ed 001 --year 2018 --type best --experiment soam  > log.pygeca.soam_001_2018
mv -f nocquet_soam_2018_001 /projet/gps/SOAM_PROC/2018/.
```

This file will be read from the node where OAR sent your processing. It tells:
\* reads your .bashrc configuration file so that all paths and python version are the one you want.
\* assign 1 core for your processing and kill your job if it has been running for more than 60 hours
\* gives a name to your processing. This name will be used when using the oarstat command to see that your job is actually being processed
\* gives a name for output that would appear on the screen if run from the command line
\* then defines the queues where your job can be process. A queue is basically a list of potential nodes.
\* tells where the processing will be done on the node, here this is /tmp, a directory ceaned by the sustem every day
\* the next line is the actual command for doing the processing
\* finally the processing directory is moved from the node back to where you want the result to be

The pyacs command for generating the job command file is pygeca_make_job.py. The job command file we just describe has been generated by the command:

```
pygeca_make_job.py  --dir_conf /projet/gps/geodesy/process/soam_setup --sd 001 --ed 001 --year 2018 --type best --experiment soam --queue QDR/DDR/NONE --walltime 60
```

## Submitting a job command file to OAR

This is done by the oarsub command: ::

    oarsub -S ./soam_247_2018 -t besteffort

The -t besteffort option controls your priority. besteffort means a low priority.

The oarstat command allows you to check the status of your job.

If you want to send many job at the same time, just use a combination of ls and awk: ::

    ls soam_\* | awk ‘NR>0 && NR<55{print “oarsub -S ./”$1,” -t besteffort “}’ | sh

will send the doy 1 to 54 for processing.

## pygeca_resubmit.py

Instead of the combination of ls and awk, pygeca_resubmit.py can be used.
pygeca_resubmit.py will search all processing directories, check the results and write the oarsub line if needed.
For instance, to check resubmit processing for doys 246-248 for year 2018:

```
pygeca_resubmit.py --sd 246 --ed 248 --year 2018 --experiment soam
```

The output would be something like:

```
oarsub -S ./soam_246_2018 -t besteffort
rm -Rf nocquet_soam_2018_247 ; oarsub -S ./soam_247_2018 -t besteffort
oarsub -S ./soam_248_2018 -t besteffort
```

Telling that doys 246 and 248 have no directory and will be processed, while 247 was already processed but with an error and needs to be remove before submitting the now processing.

## Check before processing: pygeca_check_gamit.py

pygeca_check_gamit.py checks that all information required for processing are OK and provides a summary.

```
pygeca_check_gamit.py -dir_conf /projet/gps/geodesy/process/soam_setup -sd 001 -ed 010 -year 2018 --experiment soam
```

## Check after processing: pygeca_check_sinex.py

You probably want to know whether all sites were correctly processed, or check your processing is up-to-date with respect to your rinex archive.
Your first need to generate a list of sinex files (actually ssc files) that you want to check:

```
ls proc_soam_0*/*ss > lss
```

Then running:

```
pygeca_check_sinex.py -dir_conf /projet/gps/geodesy/process/soam_setup -lsinex lss -type best --verbose --all
```

will provide some information about potential problems. Furthermore, if generates a command line for pygeca_redo, a tool that allows you to add new sites
to an existing processing without re-processing everything.

## Adding sites to an existing processing

This can be done with pygeca_redo.py which has the same syntax as pygeca_subnetworks.py except you have to specify the new sites to be added.
pygeca_redo_make_job.py is the same has pygeca_make_job.py but for creating a job that will add the new sites to an existing processing using pygeca_redo.py
