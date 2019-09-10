# Support for network creation based on provider network attributes #
​
## Proposer ##
​
- Vanessa Little (VMware)
- Mark Beierl (VMware)
- Matt Harper (RIFT)
- Ravi Chamarty (RIFT)
​
## Type ##
*Feature**
​
## Target MDG/TF ##
NBI, LCM, RO
​
## Description ##
The OSM instantiation parameters needs enhancement to support the following VIM specific per-VL attributes supports
​
provider-network:
   physical-network: string
   segmentation-id: uint32
​
NBI module shall validate the new OSM instantiation parameters. LCM module shalle pass the above parameters to RO during NS instantiation. OSM RO should support creation of VL based on provider-network.
​
In the case of VMware VCD, this allows creation of VL based on a specific VDC external network.
In the case of Openstack, this allows creation of VL based on a specific physical network.
​
​
## Demo or definition of done ##
Instantiate NS VL based on provider network attributes
