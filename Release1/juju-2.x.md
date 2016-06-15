# Juju 2.x #

## Proposer ##
Mark Shuttleworth
Marco Ceppi

## Type ##
**Feature**

## Target MDG/TF ##
**(Optional)**

VNF Configuration, DevOps

## Description ##
OSM R0 uses Juju 1.x for modelling VNFs. Also, OSM itself will be charmed,
making it much easier to deploy and operate both for evaluation and
production.

In Juju 2.x we gain a number of valuable capabilities:

 - **Multi-model controller**. A single instance of Juju can manage multiple
   models. This means that RIFT.io will be able to stand up multiple
   independent scenarios using a single Juju instance, rather than
   needing separate Juju controllers per scenario. This will reduce
   the footprint of OSM and improve the operations story for production
   users.
 - **Workload status**. VNF charms can provide a clear status which RIFT
   will be able to interpret and present to the user. VNF vendors will
   find it easier to express the status of their VNFs in a complex
   topology.
 - **LXD containers**. The "local" provider, which is used for devops
   iteration, moves to LXD which is a full hypervisor and offers much
   faster and more flexible local deployment operations. VNF endors will
   have a far more efficient test and dev experience providing OSM VNFDs.
 - **Multi-user controller**. A single Juju controller can track multiple
   users, who have independent access to particular models managed by that
   controller. For OSM to enter production usage we need to be able to
   offer audit and ops access at each level of the stack, and Juju 2.x
   enables this in a PCI-DSS compliant fashion.
 - **Resources**. A charm can now specify a set of resources that will be
   delivered to the charm at runtime. Common examples would be the charm's
   preferred JVM, or a docker image. Juju 2.x mediates access to these
   resources for efficiency, the net result is a greatly improved VNFD
   experience for VNF vendors.

Juju 2.0 is currently in late beta, APIs are finalised, with a final release
expected in July, so integration work can commence without having to wait.

The work involved in this change should come about naturally - initial Juju
1.x integration with RIFT was straightforward and Juju 2.x presents a cleaner
API, so we do not anticipate challenges on this front. The Canonical team is
happy to help the RIFT team with this update as part of our joint work on OSM.

## Demo or definition of done ##
This change would be somewhat invisible to end-users. It will substantially
improve the experience of VNF vendors because Juju 2.x charms have access
to important new capabilities.