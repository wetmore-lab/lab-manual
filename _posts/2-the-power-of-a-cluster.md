Section II: The Power of a Cluster

2.1: Submitting a Calculation

2.1.1. Submission a Calculation on URACIL

To run your Gaussian calculation, use the command 'g09submit' followed by the name of your '**.com**' file.

g09submit myfile.com

You can submit multiple Gaussian file at one time by using wildcards in the file names, where the following would submit all of the .com files in the current directory.

g09submit \*.com

While your jobs are running, a .running file will appear in the directory where the .com file was submitted from. It is very important to keep these files in the current directory path (i.e., do not move these files or change the name of any directories these files are in). This file is a copy of the .log file for this job which can be viewed (using vi) while the job is still running to monitor the progress of your calculation. You can also copy this file to a .log and transfer it to your Windows machine to view it in GaussView. When the job terminates, the .running file is replaced by a .log output file.

2.1.2. Optional Information

The Gaussian submit script assume a default walltime (maximum running time) of 4 hours and 10 GB of disk space. To better use our cluster resources, it is best to alter the walltime and disk space of your jobs when they are submitted. Estimates of the required walltime and disk space will be provided with each assignment.

To ask for more wall time (for example, 8 hours), add the '-wt 8h' option to 'g09submit**'.**

g09submit -wt 8h myfile.com

You can use anything in the format of 'AhBmCs' where A,B and C are non-negative integers, for the time, where any of the hour, minute or second fields can also be omitted.

To ask for more disk space (for example, 40 GB), add the '-d 40 G' option to 'g09submit'

g09submit -d 40G myfile.com

The size can be specified in gigabytes (G), megabytes (M), or kilobytes (K).

You can (of course) specify both walltime and disk space when submitting your files.

2.2: Estimating Gaussian Walltime

When beginning to perform calculations, users should request four processors for Gaussian 09 jobs and specify a significant amount of wall time. However, users must monitor the time required for their own calculations (by examining the output from the queue), and determine the most efficient use of cluster resources for their calculations. To do this, tabulate the type of calculation (frequency or single-point calculation), the number of basis functions, the cpu time and the walltime (both times can be obtained from the file returned by the queue).

Computational jobs increase with the size of the basis set. The size of the basis set can be judged by the number of basis functions. This information can be obtained from Gaussian .log files. For example, the following output from a Gaussian .log file indicates that this B3LYP/6-31G(d,p) calculation has 390 basis functions:

Standard basis: 6-31G(d,p) (6D, 7F)

There are 390 symmetry adapted basis functions of A symmetry.

Crude estimate of integral set expansion from redundant integrals=1.000.

Integral buffers will be 262144 words long.

Raffenetti 2 integral format.

Two-electron integral symmetry is turned on.

390 basis functions 693 primitive gaussians

77 alpha electrons 77 beta electrons

nuclear repulsion energy 1795.8717838438 Hartrees.

2.3: Monitoring Your Jobs

One of the ways you can monitor what jobs you have running is 'qstat'. This program will tell you the job ID number, your job priority number, the first 10 characters of your file name, the start time, queue, and number of processors requested for the job. The priority number is calculated by the queuing system (which depends on different factors like how much CPU time you have used in the past), where this number influences the order in which jobs are run.

You can also use qstat to view all of the jobs submitted to the cluster by all users by typing

qstat -u '\*'

This program can also be used to tell you the last number of jobs that have finished (for all users):

qstat -s z

There is another program 'qstatus' which can be used to monitor your jobs, which outputs the job ID number, the number of processors, the full job name, the start time, and which queue the job is running on, as well as a separate list for queued jobs. You can also use different options with this program to get different information, like viewing all of the jobs for all users

qstatus -a

To see all of the jobs for all users which are grouped by username

qstatus -ag

You can also sort your own jobs by file name

qstatus -s 'name'

There are many more options that you can use with both qstat and qstatus, where more details can be viewed by typing 'qstat -h' or 'qstatus -h'.

2.4: Deleting Jobs

To delete a job, get the jobid from qstat or qstatus and use it with the 'qdel' command.

qdel &lt;jobid&gt;

You can also delete multiple jobs by separating their job ID numbers by spaces

qdel &lt;jobid1&gt; &lt;jobid2&gt;

Also, if you want to kill a number of jobs that have a similar filename, (for example, if you have u_his_0 and u_his_30, and u_his_60 running) you can use to following commands to delete these jobs

qdel 'u_his_\*'

Finally, if you want to delete all of the jobs that you have running, you can use the following command

qdel -u user.name

2.5: Output from the Queue

When a job has finished, the .log file is copied from the computer the calculation was running on to the directory from which the job was submitted to the queue. Another file will also appear which has an extension .gstdout. This file contains error messages if the job did not finish normally. It also contains information about where the job was run and the length of time the job ran. For example, water.gstdout:

## g09submit v2010.06.25

## Memory: 256M

## NCores: 4

## MaxDisk: Default

## Walltime: Default

## Execution Dir: /home/stacey.wetmore

## \----

## JobID: 34827

## Execution node: compute-1-18

## \----

## Submit time: Mon Jun 28 13:33:23 MDT 2010

## Start time: Mon Jun 28 13:33:27 MDT 2010

## \----

## g09 Exit Value: 0

## Copying back authoritative .log file

## Copying back checkpoint file(s)

## \----

## End time: Mon Jun 28 13:33:34 MDT 2010

## Running time: 0h 0m 7s

## This job was run on compute node 1-18. A wall time of 4 hours was requested with 10 GB of disk space (both default values from the queue). However, the job only ran for 7 seconds. This information should be tabulated so that users can make better estimates of required wall times for future calculations

You can also estimate how much disk space was used in your calculation by examining the .log file. For example, at the bottom of water.log:

Job cpu time: 0 days 0 hours 0 minutes 11.5 seconds.

File lengths (MBytes): RWF= 5 Int= 0 D2E= 0 Chk= 1 Scr= 1

Normal termination of Gaussian 09 at Mon Jun 28 13:33:34 2010.

The file lengths (when summed together) tell us how much disk space was used for the calculation (in MB). Therefore, an optimization on water needs at least 7 MB of disk space. This information can be tabulated with the type of calculation, the number of basis functions, and the wall time to better estimate how many resources should be requested.