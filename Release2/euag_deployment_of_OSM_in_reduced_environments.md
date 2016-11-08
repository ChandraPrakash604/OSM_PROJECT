# Deployment of OSM in reduced environments #

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
UI, SO, RO, VCA

## Description ##
Currently OSM requires 8 CPUs and 16GB RAM to run. This makes really complicated 
for observers and initial testers to use OSM for the first time. Being able to 
run OSM in a reduced environment with less required resources would ease the 
first time use.

As a reference, the target should be 2CPUs and 4GB RAM for running the whole OSM 
(RO, VCA, SO, UI). In that way, OSM could run in a laptop or in a Virtualbox VM 
without problems.

In addition, in order to test the deployment of the NS, it would be required to 
run a VIM and compute nodes in a reduced setup. The use of LXD containers as 
compute nodes fits well with this idea. A single host with LXD containers and 
Linux bridges could be used as datacenter for this testing purpose, being able 
to deploy simple NS on that single host. The reference target of CPU and memory 
resources for this single host running LXD containers could be 2CPUs and 4 GB 
RAM.

## Demo or definition of done ##
N/A
