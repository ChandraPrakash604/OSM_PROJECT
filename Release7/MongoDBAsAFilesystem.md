# MongoDB as a Filesystem #

## Proposer ##
Adam Israel (Canonical)
David Garcia (Canonical)
Eduardo Sousa (Canonical)

## Type ##
**Feature**

## Target MDG/TF ##
NBI, LCM

## Description ##
Kubernetes orchestration of OSM Services has shortcomings since NBI and LCM require a 
shared volume to pass VNFD packages between them. This allows them to share the files 
between them without a major hassle. In order for this to be possible, Kubernetes needs 
to be deployed with a storage provider that supports read-write-many volumes so that 
both components can use the shared files. This puts the burden in the Kubernetes deployment.

This feature aims to reduce this dependency of the Kubernetes deployment to provide a 
shared volume by using MongoDB to share the files between the two components. The MongoDB 
as a Filesystem can be achieved by using MongoDB in conjunction with GridFS and storing 
the files as documents in MongoDB.

## Demo or definition of done ##
* The files are written to MongoDB.
* OSM is capable to instantiate a NS and make use of VNF configuration primitives.
