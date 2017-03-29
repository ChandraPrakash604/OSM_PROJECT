# Support of Physical Deployment Units in a VNF #

## Proposer ##
- Gerardo Garcia (Telefonica)
- Alfonso Tierno (Telefonica)
- Francisco Javier Ramon (Telefonica)

## Type ##
**Feature**

## Target MDG/TF ##
SO, RO

## Description ##
**This feature obsoletes feature #641: https://osm.etsi.org/gerrit/#/c/641/**

This feature aims to enable the use of Network Functions where some of their 
Deployment Units are physical (Physical Deployment Units - PDUs), so both pure 
VNFs, pure PNFs and hybrid network functions can be seamlessly supported in an 
interchangeable manner in a NS.

This feature is also expected to require a specific procedure to add PDUs to a 
catalog per datacenter, where details of their type (so that they can be 
pooled. e.g. GPU model),  location (datacenter), reachability (e.g. IP 
address), physical connections to the site (e.g. switches and ports where the 
PDU is connected), etc. can be provided.

In this phase, it will be assumed that, on time of instantiation, these PDUs 
would map 1-to-1 to VDU instances (or equivalent). In this phase, the same PDU 
cannot be used twice (in the future we might review this approach).

## Demo or definition of done ##
- Successful onboarding of a (V)NF that has 1 VDU and 1 PDU. For instance, in 
the (V)NF, the VDU could be an SDN controller and the PDU a small physical 
switch.
- Addition a PDUs in datacenter A of a given type.
- Successful deployment of a NS with the (V)NF in datacenter A.
- Unsuccessful deployment of a second instance of the same NS in the datacenter 
A (not enough resources available of that PDU type).
- Unsuccessful deployment of the same NS in another datacenter (no PDUs of that 
type available).