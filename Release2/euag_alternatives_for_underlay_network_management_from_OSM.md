# Alternatives for underlay network management from OSM #

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
RO, UI

## Description ##
Most common VIMs (Openstack, VMware, AWS) do not provide management of native L2 
underlay connections (E-Line, E-LAN) suitable for EPA. In the case of Openstack, 
there are proprietary solutions based on neutron ML2 plugins for the 
connectivity of SR-IOV interfaces. However, those solutions are not suitable for 
all use cases:

* It is not possible to connect PT (pass-through) NIC interfaces (there are no 
neutron ports associated to PT interfaces).
* It is also impossible to connect multitenant VNFs (using VLAN tags per tenant) 
with single tenant VNFs, where the VLAN tag must be automatically removed/added 
by the network.

The proposal is to enable OSM to manage underlay networks directly through an 
SDN controller (SDNC) whenever that feature is not provided by the VIM. In those 
cases, the VIM would only in charge of the creation of VM instances and the 
creation of overlay networks, while the SDNC, governed by OSM (the RO, in this 
case), would be in charge of the creation and deletion of underlay networks.

It is devised that OSM should get from the VIM the physical allocation of the 
interfaces (SRIOV, PT) once the VM is deployed, and it will command the SDNC to 
connect these interfaces in E-Line or E-LAN networks. Common SDNCs that are 
expected to be supported should be ODL and ONOS.

## Demo or definition of done ##
N/A
