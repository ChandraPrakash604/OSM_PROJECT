# Support displaying error messages from RO/VCA #

## Proposer ##
Rajesh Velandy (RIFT.io)

## Type ##
**Feature** (do not modify)

## Target MDG/TF ##
UI, SO, RO,  VCA

## Description ##
When there are errors during SO->RO or  SO->VCA interactions, the SO shall capture that error and 
expose the error through the notrthbound managemenent interface.
When an operation  instantiation/configuration result in an error, the UI shall display the error 
message returned by SO.


## Demo or definition of done ##
Should demonstrate the following:
1.Create an NS that results in an error in  RO and demonstrate that the errors are shown in the UI.
2.Create an NS that has a bad charm and  demostrate that the UI  shows the error message from VCA.