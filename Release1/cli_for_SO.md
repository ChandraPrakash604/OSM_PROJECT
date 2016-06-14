# CLI for SO #

## Proposer ##
**EUAG**

## Type ##
**Requirement**

## Target MDG/TF ##
SO

## Description ##
Availability of a CLI client to use the northbound interface of the SO, thus
easing the testing activities and facilitating the development cycle with
Jenkins. Besides, the tool will be used by the end user as an alternative way to
interact with OSM.

The CLI program should implement at least the following commands:

- Configuring RO parameters (Cloud account in current terminology)
- Configuring CM parameters (Config account in current terminology)
- Adding a VNF package to the catalog
- Adding an NS package to the catalog
- Deleting an NS package from the catalog
- Deleting a VNF package from the catalog
- Launching NS instance with specific parameters (e.g. destination datacentre per VNF, VNF instance name)
- Invoking a service primitive of an NS instance
- Deleting NS instance

## Demo or definition of done ##

The program must be used in a test to:

- configure the RO and the CM,
- onboard at least 1 VNF,
- onboard at least 1 NS, consisting of 2 VNFs interconnected
- instantiate the NS with specific parameters (destination datacentre per VNF, VNF instance name)
- invoke an NS primitive involving the 2 VNFs,
- check the result from the primitive in the 2 VNFs,
- delete the instance,
- delete the NS package, and
- delete the VNF package.

