# Network types in RO #

## Proposer ##
- Gerardo García (Telefónica)
- Alfonso Tierno (Telefónica)

## Type ##
**Requirement**

## Target MDG/TF ##
RO

## Description ##
Current network types in RO describe the actual enforcement done in the host bridges/switches and
in the physical switches. This feature suggests changing the network types in RO functions and
databases to describe, instead of the actual enforcement, the functional behaviour.

Today network types in RO are:

- ptp, for point-to-point networks (E-Line) enforced in an underlay switching infrastructure. VM
interfaces must be either port passthrough or SR-IOV.
- data, for L2 networks (E-LAN) enforced in an underlay switching infrastructure. VM interfaces
must be data plane interfaces (either port passthrough or SRIOV).
- bridge, for L2 networks (E-LAN) enforced in a Linux Bridge or OVS-based virtual switch. VM
interfaces are based on virtio interfaces.

New network types would be:

- "E-Line", for E-Line networks, independently on the kind of enforcement in place. E-Line networks
are L2 point-to-point networks which meet that whatever frames come from a network port goes to the
other network port, and viceversa, no matter the MAC addresses behind.
- "E-LAN", for E-LAN networks, independently on the kind of enforcement in place.E-LAN networks are
L2 point-to-multipoint networks where the destination network port is determined by the destination
MAC address.

Both kinds of networks would have a parameter related to the type of enforcement (e.g. virtual
networks or underlay) that could be specified by the NS builder or by the VNF builder to make the
enforcement explicit. If specified, the specific network configuration will be done either via
virtual networks (Linux bridges or virtual switches, depending on the technology used by VIM) or
via underlay switching infrastructure. If unspecified, the enforcement will depend on the actual
interfaces being connnected. For the moment, with the current state of the art in VIMs, it is
assumed that:

- An E-Line network cannot connect VM interfaces based on virtio, but can only connect data plane
interfaces (port passthorugh or SRIOV).
- An E-LAN network can only connect VM interfaces of the same type: either virtio interfaces or
dataplane interfaces.

As an example, if 3 virtio-based VM interfaces are connected in an NS or VNF to an E-LAN network,
the enforcement will be done via virtual networks based on Linux bridges or OVS, depending on the
specific technology used by the VIM, but they won't be connected via the underlay switching. On the
other hand, if 2 virtio-based VM interfaces and 1 SRIOV are intended to be connected in an NS, this
will be rejected by the RO at instantiation time. This behaviour could be changed in the future if
the state of the art in VIMs evolve.

In addition, E-LAN networks can have extra parameters to be passed to the VIM during network
creation such as L3 configuration parameters (e.g. DHCP enabling, DHCP range, FW enabling, FW rules
to be applied, IPv4 subnet and mask, etc.). The internal data structures in RO should allow room
for potential addition of new parameters, but the specification of these extra parameters is out of
the scope of this feature request.

The following changes are devised in RO:

- openmano\_schemas.py: changes in schemas to support the new types of networks and their
parameters.
- nfvo.py: changes in all functions where actions are taken over networks (network creation in the
context of a VNF or an NS, network deployment in VIM, read network information, etc.).
- MySQL DB: changes in tables related to networks at VNF or NS level.
- nfvo\_db: changes in functions to update the DB tables accordingly.
- http\_server.py: changes in REST methods dealing with networks (Create, Read and Update
operations) to take into account the changes in schemas, nfvo functions and nfvo_db functions.

Further investigation will be required to measure precisely the implications in code development.

Changes in RO will affect its north-bound interface, thus implying changes in SO and also
potentially in the data models for VNF and NS. If this feature is accepted, additional requirements
and specs might be required in the SO to guarantee interoperability between RO and SO.

## Demo or definition of done ##
The following tests are suggested:
- Success test for an NS deployment with single-VM VNFs. The NS will have at least 2 VNFs connected
with E-LAN and E-Line networks.
- Success test for an NS deployment with a multi-VM VNF. The multi-VM VNF will have at least 2 VMs
connected with E-LAN and E-Line networks.
- Failure test for an NS deployment with single-VM VNFs. The NS will have at least 2 VNFs connected
with E-LAN and E-Line networks. The type of interfaces connected to the E-LAN or to the E-Line
networks will lead to a failure.
- Failure test for an NS deployment with a multi-VM VNF. The multi-VM VNF will have at least 2 VMs
connected with E-LAN and E-Line networks. The type of interfaces connected to the E-LAN or to the E-Line networks will lead to a failure.

