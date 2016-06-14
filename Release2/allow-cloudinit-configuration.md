# Allow cloudinit configuration #

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
UI, RO, SO

## Description ##
Currently, OSM cannot leverage on the traditional metadata "cloud-init" procedures, commonly used
in cloud environments. "cloud-init" is typically used for the initial configuration of virtual
machines where the user can inject context information (configuration parameters and scripts) to
grant the initial VM setup.

This configuration can be independent of the initial SO configuration.

The specific configuration can be defined at 3 levels:

1. A VNFD can contain cloud-init metadata (configuration parameters and scripts) for each VM.
2. An NSD can override this metadata for each one of its VNFs.
3. Finally, the end user can override this metadata at instantiation time.

In order to have this feature implemented, the following changes are devised:

- In the UI:
    - The end user can see/edit the metadata information for every virtual machine at instantiation
    time
- In the RO:
    - Database changes to annotate instance-related information.
    - Changes in northbound API to allow that information.
    - Changes in VIM connector to transmit this information.
- In the SO:
    - VNFD and NSD data models should incorporate this information
    - Connection to RO must be modified accordingly to the changes in RO northbound API.
    - Database changes to annotate this information.


## Demo or definition of done ##
The test consists in the deployment of an NS instance, where user-defined scripts have been
injected as cloud-init metadata. The user-defined scripts can be injected at different levels: VNFD
level, NSD level and NS instance level. The test should do as many deployments as level
combinations are possible.

The test is considered successful if the appropriate script is executed (it could be a simple
"touch file").
