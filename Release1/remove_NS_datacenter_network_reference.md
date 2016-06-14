# Remove explicit datacenter network reference at the NS descriptor#

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
UI, RO, SO

## Description ##
In the current implementation a NS descriptor (NSD) contains "external" networks, or connection
points intended for  connecting outside. Management networks are clear examples of these
connections, but they can be also dataplane connections. These networks must exist at the VIM with
the same name used for the NSD. This relationship between descriptor name and deployment is
undesirable because it forces to have particular NSD for each VIM where it will be deployed.

The user must be able to map what VIM network is used for a concrete NSD "external" network or
connection point. The user must have the following options:

- map a NSD "external" network name to an existing VIM network.
- create a new network at the VIM. In this case this network will not be used to connect outside,
but this is still useful for testing purposes. Also a later NSD deployment can use the created
network so that both deployments are connected among them.

In addition to these options, an automated mapping is also desirable. When a VIM is registered at
OSM, it can be indicated particular mappings between NSD external networks names and the existing
VIM networks. If this mapping exist, it applies automatically if the user has not indicated other
action. This is specially useful for management networks, so that the VIM management network is
indicated once at registration, avoiding the user to indicate the VIM management network every time
he makes a deployment.

In the case that the RO has not enough information for mapping a "external" NSD network or
connection point at deployment time, it will reject the instantiation.

In order to have this feature implemented, the following changes are devised:

- In the UI:
    - The end user should have the possibility to select an option for each "external" NSD network
    or connection point. The options can be "manual mapping" (it is desirable to show the list of
    existing VIM networks), or "create the network".
- In the RO:
    - Allow this information at the instantiation time. The NS instance should allow to specify
    these parameters.
    - Database changes to annotate instance-related information, in this case the VIM network used.
    - Changes in northbound API to allow that information
- In the SO:
    - NS data models should incorporate a data model for instances, different than the NS data
    model for templates, where it should be possible to the network instance-related parameters.
    - Connection to RO must be modified accordingly to the changes in RO northbound API.


Specs for each module are to be written. For instance, in RO the spec is expected to include the
following devised changes:

- openmano_schemas.py: changes in schema "instance_scenario_create_schema" to support the
specification of network mapping information.
- nfvo.py: changes in function "create\_instance" to support the new schema and take the actions
accordingly, including the appropriate calls to nfvo\_db functions.
- MySQL DB: changes in "instance\_nets" table is required. Further investigation is required.
- nfvo\_db: changes in functions to update the previous tables accordingly.
- http\_server.py: changes in http\_post\_instances to take into account the changes in schemas,
nfvo functions and nfvo\_db functions.

## Demo or definition of done ##
A test case consisting of the deployment of the same NSD at two different VIMs, where  the name of
an external network used for mapping a NSD network are different.
Both the manual and automate mapping must be tested.
Finally choose the option of "create network" for a first NSD deployment, and the option of using
this created network for a second NSD deployment. Ensure that both deployments are interconnected.

