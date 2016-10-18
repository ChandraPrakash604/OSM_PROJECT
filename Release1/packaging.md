# R1 Packaging #

## Proposer ##
Jeremy Mordkoff (RIFT.io) 

## Type ##
**Feature**

## Target MDG/TF ##
DevOp


## Description ##
* tools for managing packages – generating, pushing and pulling packages into workspaces, signing, 
promoting and publishing releases
** a way for the host based scripts to copy artifacts from the container to a common area on the host (I call it the host but it is really the VM at OSM).
** a new host based script that can create the debian signatures on the packages and create a local debian repository
** a new host based script that can promote a set of packages from the latest repository to the stable repository
** a new host based script that can rsync the local debian repositories to the OSM public server
** a way to access either the local or the OSM public debian repository from inside a container

* branch support
**  We will need to teach the gerrit job in jenkins how to verify a R1.0 patch
** We will need to jenkins job to merge R1.0 to master after verifying there are no 
conflicts and that it builds. 
** The installer should have the option to use the latest 1.0 code or the latest master (2.0) 
code instead of the v1.0.0 code.

## Demo or definition of done ##
sucessful installation of OSM using only packages
