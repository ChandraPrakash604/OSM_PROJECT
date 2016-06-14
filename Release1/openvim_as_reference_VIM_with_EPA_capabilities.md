# OpenVIM as reference VIM with EPA capabilities #

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
No OSM module is targeted. RO might be considered as the appropriate target MDG for the moment.

## Description ##

Although OSM is not covering the VIM component of the MANO stack, one of the main goals of OSM is
to demonstrate that it is possible to deploy VNFs that leverage on Enhanced Platform Awareness
(EPA) to obtain predictable performance. Well-known VIMs today lack of capabilities such as the use
of passthrough interfaces for the VMs or the creation of E-Line L2 networks based on these
passthrough interfaces.

It would be desirable that OSM integrates a reference VIM that exposes EPA capabilities for the
creation of VMs with such specific EPA requirements. OpenVIM is able to expose EPA capabilities
such as:

- Use of hugepages memory
- Pinning to HW threads or cores
- Simultaneous support of SR-IOV and passthrough interfaces
- Differentiaton between E-Line and E-LAN L2 networks
- Configuration of an underlay switch for inter-VM communication via Openflow pro-active rules
through an SDN controller (currently OpenDaylight, Floodlight)

OpenVIM has been used for OSM MWC demo in order to deploy dataplane VNFs. It is available for free
usage in GitHub under Apache 2 license
([OpenVIM in GitHub](https://github.com/nfvlabs/openvim "OpenVIM")). Its use as VIM with EPA
capabilities is required for testing EPA deployments in OSM, at least as long as there are no other
known VIMs with EPA capabilities.

The inclusion of OpenVIM in OSM Release 1 will help those providers developing dataplane VNFs to
use a development environment seamlessly integrated with OSM, leveraging on the pre-exisiting
integration of OpenVIM with OpenMANO.

While it is possible today to use OpenVIM from OSM Release 0, the inclusion of OpenVIM in OSM
Release 1 will ease its adaptation by the OSM Community to add new capabilities that might be not
part of OpenVIM yet, guaranteering seamless interoperability.

## Demo or definition of done ##

- OpenVIM contributed to OSM repos with Apache 2 license.
- Seamless interoperability of OpenVIM with the rest of OSM components at the end of Release 1.

