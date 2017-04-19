# support cloud_init to inject ssh keys in VMware Connector #

## Proposer ##
Vanessa Little (TDC,VMware)

## Type ##
**Feature**

## Target MDG/TF ##
RO

## Description ##
Add support for cloud-init  definition in vmware connector to inject ssh keys,
using VMware post config features.


## Demo or definition of done ##
Definition of Done: After a VM is deployed with cloud_init ssh key definitions,
VM is reachable over ssh using those keys once deployment has completed.