# Throw network failed if VNFD has incomplete IP profile. #

## Proposer ##
Vanessa Little (TDC,VMware)

## Type ##
**Feature**

## Target MDG/TF ##
RO

## Description ##
Error handling:  Throw network failed error message if VNFD has incomplete IP profile.


## Demo or definition of done ##
Definition of Done:  'network failed' error message is thrown if VNFD has incomplete 
profile when VNF is instansiated via vimconn_vmware.py