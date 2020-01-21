# Re-enable NS primitives #

## Proposer ##
Adam Israel
Gerardo Garcia

## Type ##
**Feature**

## Target MDG/TF ##
IM, LCM, N2VC, NBI, osmclient

## Description ##
With the new OSM internal architecture, support of NS primitives based on
scripts, offered in the past by the SO, has disappeared. Enabling again NS
primitives is required to allow day-1 and day-2 operations over NS.

Due to the need to implement it from scratch, it is better to follow an approach
for NS primitives similar to VNF so that the same procedures and code could
be used. Moreover, similar constructs for VNF and NS primitives enable a
natural path for nesting NS, where a NS can be considered as a VNF building
block to construct other NS. In this regard, the IM changes for NS primitives
(primitives, charms, relations) should be as similar as possible to the ones
currently present in the VNFD and VNFR IM.

## Demo or definition of done ##
To be added.
