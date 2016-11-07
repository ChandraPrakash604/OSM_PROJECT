# Composer Reference Lists #

## Proposer ##
- Rajesh Velandy


## Type ##
**Feature**

## Target MDG/TF ##
UI, SO

## Description ##

NSD and VNFD have many cross-references, For example,
 - NSD has constituent VNFD id references
 - VLD has VNFD connection point references

Composer presents references as inputs, forcing the user to copy/paste id references.

Composer should present these references as dropdown lists.

Reference lists should update dynamically in composer as the model is modified.

The types on some model attributes need to be changed from string to leafref in the model.


## Demo or definition of done ##
Demonstrate the resolution of leafrefs in the GUI.
