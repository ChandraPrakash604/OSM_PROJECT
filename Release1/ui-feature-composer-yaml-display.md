# Support YAML display of descriptor in Composer #

## Proposer ##
Kiran Kashalkar (RIFT.io)

## Type ##
**Feature** (do not modify)

## Target MDG/TF ##
UI

## Description ##
Currently the Composer has an option of showing the JSON representation of a
descriptor that's being created/edited.
Now that we support YAML format for descriptors, the JSON viewer will be
converted to a YAML viewer as YAML is more human-friendly.
This will be offered as a purely front-end feature with no support from the SO.


## Demo or definition of done ##
Demonstrate the following:
1. A user should be able to view the YAML format of a descriptor that was
 onboarded using the Catalog Manager.
2. A user should be able to view the YAML format of a descriptor that he/she has
 created using the Composer.
3. A user should be able to view the YAML format of a descriptor that he/she is
 editing, irrespective of whether the original descriptor was onboarded using
 the catalog manager or created using the Composer.