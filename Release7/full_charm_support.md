# Non-Proxy charms #

## Proposer ##
- Adam Israel

## Type ##
**Feature**

## Target MDG/TF ##
RO, SO, VCA

## Description ##

Support for VNFs that are installed and configured via a Juju charm, using a standard Ubuntu cloud image.

### Implementation

This feature requires modification to the current workflow used by the SO:

1. SO asks RO for an instance (typically an appliance VM)
2. RO provides the SO with a new VNF instance (ip address, etc.)
3. SO deploys VNF proxy charm
4. SO configures VNF proxy charm
5. Optionally, SO executes service primitives against the VNF charm

Proposed workflow:

1. SO asks RO for an instance (a cloud image uploaded to the VIM)
2. RO provides the SO with a new instance (ip address, etc)
3. SO adds instance to VCA (using Juju's manual provider)
4. SO deploys VNF charm to instance, which installs and configures the VNF
5. Optionally, SO executes service primitives against the VNF charm.


## Demo or definition of done ##

This feature is considered complete when any charm from JujuCharms.com can be deployed within OSM.
