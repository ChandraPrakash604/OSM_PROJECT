# Support of high level primitives in SDN plugin model for SDN assist #
 
## Proposer ##
- Gerardo Garcia (Telefonica)
- Alfonso Tierno (Telefonica)
- Francisco Javier Ramon (Telefonica)
 
## Type ##
**Feature**
 
## Target MDG/TF ##
RO
 
## Description ##
The SDN plugin model in OSM assumes the existence of a set of calls in the 
plugin that allow RO to interact with different but equivalent primitives from 
various SDN controllers in an homogeneous fashion.

The current set of calls assumes the availability of a number of basic 
flow-level provided by the SDN Controller, letting the RO assume the logic to 
create the various kinds of underlay networks supported by OSM, namely E-Line 
and E-LAN types.

While this model of use might be a reasonable approach for many cases, it might 
be suboptimal for modern SDN controllers, which can be already capable of 
providing high level API operations to set up E-LAN and/or E-Line connections 
(and even prevent the use of flow-level operations.

This feature proposes to augment the current SDN plugin model to support also 
CRUD operations for complete networks, leveraging on existing API calls of 
modern SDN controllers.

## Demo or definition of done ##
Show that it is possible to create, read, update and delete underlay 
connections of E-LAN and E-line types with, at least, one of the supported 
types of SDN controllers.