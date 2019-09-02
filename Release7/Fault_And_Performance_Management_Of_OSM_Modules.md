# Fault and Performance Management of OSM Modules #

## Proposer ##
Jose Manuel Palacios (Minsait)
Alexis Romero (Minsait)

## Type ##
**Feature**

## Target MDG/TF ##
**DevOps**,
**Service Assurance**

## Description ##
Currently, OSM provides mechanisms for the Fault and Performance monitoring of the deployed Network Functions, by retrieving metrics from the VIM and directly from the VNFs. The monitoring of the OSM modules is done via the optional ELK stack that retrieves some metrics that are not OSM specific, but common to any kind of software, such as CPU and memory usage. Logs may also collected and stored in the ELK stack, but those are mostly unstructured and it is difficult to distill useful information using them.

In a production environment is crucial to have information about the health status and performance of the OSM modules. For that purpose those should be properly instrumented, exporting the relevant metrics.

There are several reasonable choices for the instrumentation mechanism, the venerable SNMP still being the default option in telco environments. Nevertheless, since OSM already includes a Prometheus module as the repository for VNF metrics, it makes sense to leverage it also for this function.

The implementation would involve:

- Adding functionality to each one of the OSM modules so that it natively exports Prometheus metrics in a standard http "/metrics" endpoint. *The list of metrics for each module should be defined in an activity prior to the start of the implementation.*
- Including, in the OSM distribution, the appropriate Prometheus adapters for the third party software, namely Mongodb, Kafka and MariaDB/MySql.
- Creating a set of standard alarms based on the exported metrics, which may be later extended and customized based on specific operator needs. *The list of standard alarms for each module should be defined in an activity prior to the start of the implementation*.

This approach makes particular sense in a Kubernetes based OSM deployment using  [Prometheus Operator](https://github.com/coreos/prometheus-operator), which will facilitate the dynamic discovery of the OSM module instances and the reaction to node failures, thus achieving almost Zero touch operations in this regard.

Points for additional discussion:

- Whether this should be an optional component.
- Usage of the same Prometheus instance as for VNF monitoring, or a dedicated one.
- How to restrict access based on user roles (this is also relevant for the current VNF metrics)
- Definition of the metrics and alerts to be created for each module.


## Demo or definition of done ##

As part of the installation of the OSM distribution, the metrics for all the OSM modules (including third party software) should be available in Prometheus and may be visualized using a general purpose tool such as Grafana.