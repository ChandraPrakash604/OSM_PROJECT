# Overlay network connectivity in Openvim with OVS instead of Linux Bridges #

## Proposer ##
- Alfonso Tierno (Telefonica)
- Gerardo Garcia (Telefonica)

## Type ##
**Feature**

## Target MDG/TF ##
RO

## Description ##
OpenVIM currently uses pre-provisioned Linux bridges to create the overlay
networks used to interconnect the VMs. Those Linux bridges are built on a host
interface and are associated with a VLAN tag, which is used to transport frames
between VMs located in different hosts across a switching infrastructure.

Linux bridges, while working well in practice, have limitations (e.g. VLAN as
the only mechanism for achieving isolation). It also lacks some advanced
capabilities (L3 filtering, IP tunneling, support of Openflow rules, etc.).

Open vSwitch (OVS) (http://www.openvswitch.org/) provides those advanced
capabilities and would be better aligned with future OSM needs and use cases.

This feature proposes the support of OVS in openvim as an alternative to Linux
Bridges. Openvim installer and configuration files should provide options to
use either Linux Bridges or OVS. Scripts for automatic configuration of hosts
should also provide that option.


## Demo or definition of done ##
N/A
