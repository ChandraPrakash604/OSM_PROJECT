# Multi-site NS - support of NS instances with VNFs running in different datacenters#

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
UI, RO, SO

## Description ##
This feature request is about supporting NS instances with VNFs running in different datacenters.

This feature assumes that the networks interconnecting several datacenters are pre-preprovisioned
(this pre-provision is out of the scope of this feature request).

Current implementation in Release 0 allowed the deployment of a Network Service instance in the
datacenter chosen by the user. Specifically the MWC demo covered 4 deployments and the user decided
for every deployment the datacenter where to deploy.

However, it is not possible to span an NS instance across different datacenters on a single
scenario (e.g. with some VNFs running in datacenter A and others in datacenter B). The workaround
of splitting the NS descriptor and deploy at different datacenters is not valid as it does not
allow to have common NS service primitives.

There are several use cases where a multi-site NS applies, e.g.:

- The deployment of a full core network with several PEs in different datacenters.
- The deployment of VoIP network where some elements are centralized in a datacenter while others
are distributed (e.g. SBC).

In order to have this feature implemented, the following changes are devised:

- In the UI:
    - The end user should have the possibility to select for each VNF the specific datacenter where
    it will be instantiated.
    - If required, the end user should be able to select for each network in the NS the specific
    datacenter where it will be instantiated.
    - In case of networks spanning across several datacenters (e.g. an E-Line connecting a VNF in a
    datacenter to another VNF in a different datacenter), the end user must select for each network
    edge which one of the existing datacenter networks has to be used.
- In the RO:
    - NS data models should differentiate between the data model for instances and the data model
    for templates. The NS instance should allow to specify instance-related parameters for VNFs (in
    this case, destination datacenter, but others can be added in the future, e.g. VNF instance
    name). Additionally, the NS instance should allow to specify instance-related information for
    networks:
        - If the network is a single-DC network, i.e. it connects VNFs from the same datacenter,
        there is no need to indicate the datacenter where the network will be deployed, since it
        will be implicit from the VNFs.
        - If the network is an inter-DC network, i.e. it connects VNFs from different datacenters,
        the instance related information will include, for each network edge, the existing
        datacenter network to be used.
    - Database changes to annotate instance-related information, in this case the datacenter (or
    datacenters) where it was deployed.
    - Changes in northbound API to allow that information
- In the SO:
    - NS data models should incorporate a data model for instances, different than the NS data
    model for templates, where it should be possible to specify VNF instance-related parameters (in
    this case, destination datacenter, but others can be added in the future, e.g. VNF instance
    name).
    - Connection to RO must be modified accordingly to the changes in RO northbound API.
    - Database changes to annotate instance-related information, in this case the datacenter where
    it was deployed.

Specs for each module are to be written. For instance, in RO the spec is expected to include the
following devised changes:

- openmano\_schemas.py: changes in schema "instance\_scenario\_create\_schema" to support the
specification of instance-related information per VNF and network.
- nfvo.py: changes in function "create\_instance" to support the new schema and take the actions
accordingly, including the appropriate calls to nfvo\_db functions.
- MySQL DB: changes in "instance\_scenarios", "instance\_vnfs", "instance\_vms" and
"instance\_nets" tables are required. Further investigation is required.
- nfvo\_db: changes in functions to update the previous tables accordingly.
- http\_server.py: changes in http\_post\_instances to take into account the changes in schemas,
nfvo functions and nfvo\_db functions.

## Demo or definition of done ##
A test case consisting of the deployment of an NS instance with 2 interconnected VNFs (A and B) is
suggested. As a pre-requirement, there must be 2 datacenters (DC1, DC2) interconnected through a
pre-provisioned network visible at RO. As a convention, the network in DC1 will be named
DC1-interDC-net and the network in DC2 will be named DC2-interDC-net.

At instantiation time, in a single transaction (e.g. launched from the GUI or the CLI), the NS
instance must be deployed specifying that VNF A is deployed in DC1 and VNF B in DC2, VNF A is
attached to DC1-interDC-net, and VNF B is attached to DC2-interDC-net.

Information in both RO and SO should be read after the deployment to check validity of the test.
