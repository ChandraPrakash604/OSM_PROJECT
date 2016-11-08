# Distribution of OSM SW as Docker container images #

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
UI, SO, RO, VCA

## Description ##
OSM SW distribution is currently done as source code, which is downloaded by an 
installer, which also creates several LXD containers for each component, and 
builds the SW on those containers.

Docker containers provide an appropriate framework to separate the different 
processes of a system in individual process containers so that the system 
becomes much more flexible in field (for instance, HA or scale-out strategies 
for an OSM system might be quickly aligned with the state of the art). With the 
Docker approach, you get freedom to deploy each process in a different place, 
scale them independently, design your own approach for High Availability, etc.

This feature proposes the separation of the different OSM processes in Docker 
container images. Here the use of the term ''process'' instead of ''component'' 
is intentional. '''Processes running on each component must be identified and 
Docker containers must be created per process and not per component'''.

## Demo or definition of done ##
N/A
