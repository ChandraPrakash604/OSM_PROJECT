# Access to VNF console #

## Proposer ##
**EUAG**

## Type ##
**Feature**

## Target MDG/TF ##
UI, SO, RO

## Description ##
Current implementation for Release 0 does not allow remote access to the VNF console (actually, any
of the consoles of the VMs integrating the VNF). This kind of access from the OSM GUI to the VNF
console is desirable as a last resort.

With PNFs today, access is typically done through telnet or ssh to configure a PNF. Through that
process, it is possible to get access to a specific console that is not the typical Linux root
Shell, but a different one exposing only specific configuration parameters.

With VNFs, two different approaches have been found:
- In some cases, the access to the UI is through telnet or ssh in a similar way to PNFs.
- In other cases, as a last resort, the access could be through a terminal accesible via VNC or
spice, in a similar way to any other guest VM in the cloud.

This feature request is about the second approach: access to terminal via VNC or spice.

Two different situations are foreseen depending on the kind of VNF:

- Single-VM VNFs. Access to the VNF console is equivalent to access to the VM console
- Multi-VM VNFs:
    - There is usually a VM for management purposes (OAM VM). Access to the VNF console would be
    equivalent to access to the OAM VM.
    - The operator will typically want to access the OAM VM of that multi-VM VNF, because from that
    VM it is possible to configure the whole VNF. However, under some circunstances (e.g. tests
    with VNF provider), it might be helpful to have access to every VM of a multi-VM VNF. Although
    its use would be less frequent for the end user, this is still an interesting feature to have
    for troubleshooting purposes.
    - In order to distinguish the console of the OAM VM from the rest of consoles, it should be
    possible that the VNF descriptor allowed to identify the VM whose console will be used as VNF
    console.

It is clear that, this feature requires the VIMs to be capable of creating terminals based on VNC
or Spice. The VIM must build a URL for accessing the terminal through the hypervisor and, moreover,
this URL must be exposed to RO.

The RO should read the URL of the VM consoles from the VIM and expose it to SO. The SO should offer
that URL to the UI. The UI should present that URL to the end user so that he/she can just click on
it and launch the appropriate application to access the VNF console. Ideally, the application
console could be integrated with the UI, so that all consoles are opened as tabs in the UI.

From the UI perspective, it is expected that:

- The end user can inspect the VNFs running in an NS and click on any of them to open the VNF
console. A dedicated button is suggested to open that console.
- In case of a multi-VM VNF, besides the possibility to open the VNF console (equivalent to the OAM
VM), the end user could inspect the running VMs and click on any of them to open the console of the
VM. A dedicated button is also suggested to open that console.

## Demo or definition of done ##
A test case consisting of the deployment of an NS instance with 2 interconnected VNFs (A and B) is
suggested. Both VNFs can be deployed in the same datacenter. VNF A might be a single-VM VNF, while
VNF B might be a multi-VM VNF.

From the UI, it should be possible to access to the following consoles:

- Console of VNF A
- Console of VNF B
- Console of all VMs integrating VNF B

