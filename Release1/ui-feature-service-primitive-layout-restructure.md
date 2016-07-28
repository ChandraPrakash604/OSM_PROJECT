# Restructure Service Primitive Jobs Layout  #

## Proposer ##
Kiran Kashalkar (RIFT.io)

## Type ##
**Feature** (do not modify)

## Target MDG/TF ##
UI, SO

## Description ##
Currently the service primitive job details have no order, so one cannot tell
what order the jobs were executed in.
With the help of the SO to provide a timestamp (seconds since epoch) on each job indicating the
submission time, the UI should order the jobs with latest on top.
The service primitive jobs also don't have the parameters passed along with the
job, so context is lost.
Again, with the help of the SO module, the UI should show the parameters that
were used when triggering a job.


## Demo or definition of done ##
Should demonstrate the following:
1. When multiple jobs are fired, they should be displayed in reverse order of
 trigger time. i.e. latest on top.
2. Each job should display the parameters it was triggered with in addition to
 current information.