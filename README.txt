================================================================================
submitArrayJobs

General program to submit serial jobs using the LSF platform on distributed HPC
  environments


================================================================================
Written by Mario Pujato

Version: 1.2.2
Created: 032415


================================================================================
NOTE:
  Switches do not require you to input any value. For example, if you want to
   activate the "Dry run" option, you simply throw a "-d" with your
   arguments


================================================================================
USAGE: submitArrayJobs [options] <arguments>

[options]

      -C Commands file (file with commands that you wish to run, with no
          submission header)
         Allowed variables:
           DATE     is the current date in the format: MMDDYY
           CURDIR   is the current directory
           PROC     is the number of processors specified in the -n variable
           JOBNAME  is the first field in the array file
           VAR1     is the first field after the JOBNAME
           VAR2     is the second field after the JOBNAME
           VARn     is the nth field after the JOBNAME
           VARDIRn  is the directory component of the file name in the nth field
                     after the JOBNAME
           VARBASEn is the directory component of the file name in the nth field
                     after the JOBNAME

      -A Array file
         Each line corresponds to a different job (jobnames should be unique)
         Fields should be TAB-separated
         Example lines:
         jobname1	variable1	variable2	...
         jobname2	variable1	variable2	...

      -W Number of requested time before killing the job
         (default: 1:00 -h:mm-)

      -n Number of requested processors
         (default: 1)

      -M Requested memory in MB
         (default: 2000 -2GB-)

      -t (switch) Deactivate job tiling
         By default, the job is submitted to one host that has the number of
          requested processors
         WARNING: If there is no host with the number of requested processors,
          the job will be pending forever!

      -d (switch) Dry run. Scripts are created but not submitted and/or deleted
         Use this option if you want to inspect the submission scripts prior to
          submission
================================================================================
