# Unfiltered virtual interfaces in VNFs #

## Proposer ##
- Gerardo Garcia (Telefonica)
- Alfonso Tierno (Telefonica)
- Francisco Javier Ramon (Telefonica)

## Type ##
**Feature**

## Target MDG/TF ##
UI, SO, RO

## Description ##
When VLDs are created as overlay networks on an NFVI, some VIMs like Openstack
implement some security policies that apply L2-L4 filtering rules to the frames
in those networks. By default, when creating VLDs (networks in VIMs) and when
attaching VDUs to the VLDs (attaching a VM to a network in a VIM), those
security policies are created in the VIM.

Those security policies (e.g. port security in Openstack) can be disabled at a
network level or at port level in the VIM. However, this ability to disable those
security policies has not been implemented as an end-to-end option in OSM.

This feature proposes the addition of a parameter to enable or disable that port
security per VDU/VM interface. This will affect the data model for the VDU
managed by the SO, will affect the UI, which should offer the option to enable or
disable it, and will affect the RO, which should specify that capability down to
the VIMs that support it.

## Demo or definition of done ##
An end-to-end use case is required, where the user creates a VNF in the UI and
disables the filtering policy on a VM interface. Once the VNF is instantiated as
part of a NS instance, it should be checked in the VIM that the filtering policy
has been disabled in that interface/port, while in the network should be enabled.

