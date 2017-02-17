# NS Scaling #

## Proposer ##
- Gerardo Garcia (Telefonica)

## Type ##
**Feature**

## Target MDG/TF ##
UI, SO, RO, VCA

## Description ##
This feature captures the need of NS scaling use case, as discussed in
different TSC+MDL calls. The description below is a first idea to be
elaborated and discussed further.

A NS will have defined, as part of the descriptor, different ordered scale
steps, starting from number 1. For each step different groups of VNFs and VLDs
will be required.

For simplicity, the feature will assume that the trigger will be manual by
the network operator, using the UI. The trigger will specify to which scale step
the NS will move.

The action will reach the SO, which will identify the incremental additions
required in the RO and in the VCA. First, the actions to be done in the RO will be
executed, and later, the ones in the VCA.

Rollback mechanisms should be implemented E2E accross mechanisms.

Regarding the interaction between SO and RO, the following mechanism is proposed:
- The SO will turn scaling-up of a single NS events into new RO Network Scenarios
and will orchestrate them in RO.
- The SO will turn scaling-down events into Network Scenario terminations in RO.
- The SO will keep control of the different RO Network Scenarios that belong to
a NS in the SO.

## Demo or definition of done ##
N/A


