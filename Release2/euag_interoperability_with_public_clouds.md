# Interoperability with public clouds #

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
RO

## Description ##
Currently OSM can deploy VNFs in sites controlled by VIMs of the following 
types: Openstack, Openvim and VMware vCloud Director. In practice, this is 
forcing the user to have access to a VIM of one of those types, which might not
be simple for a general user that just wants to test OSM.

Being able to interact with public clouds such as AWS and Google Cloud would 
allow a general user to test OSM without the need to deploy a VIM. Moreover, 
those public clouds could be part of multi-site deployments in production.

In practice, this feature would require interacting with AWS APIs and Google 
Cloud APIs as a minimum, in a similar way as it is done with other VIMs.

## Demo or definition of done ##
N/A
