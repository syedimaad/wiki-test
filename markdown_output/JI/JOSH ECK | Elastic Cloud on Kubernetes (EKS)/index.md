## Overview

------------------------------------------------------------------------

Elasticsearch Database is a critical component of the JOSH
Infrastructure stack where different applications hold user, video and
content related meta data and data. We self-run these Elasticsearch
databases as [ECK
clusters](https://www.elastic.co/guide/en/cloud-on-k8s/current/index.html)
running on Amazon Kubernetes Service to which multiple applications and
Lambda functions connect to to store and retrieve data.

## Components

------------------------------------------------------------------------

On a high-level a typical ECK deployment on Amazon EKS is like the
following (where the use of multi-AZs, node groups count and members
varies per ECK cluster)

Following are the key systems and services that make up our ECK
ecosystem:

+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| **Component**                                                                                                                                               | **Description**                                                             |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| [EKS](https://aws.amazon.com/eks/features/#:~:text=Amazon%20Elastic%20Kubernetes%20Service%20(Amazon,and%20management%20of%20containerized%20applications.) | Managed Kubernetes service from Amazon where we run the Elasticsearch       |
|                                                                                                                                                             | workloads on EKS worker nodes. Amazon EKS supports native integration to    |
|                                                                                                                                                             | other AWS services which are required for overall system run, like:         |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | - using EBS as Persistent Volumes                                           |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | - using Elastic Load Balancing for exposing Kubernetes services             |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | - using Cloud Watch for Control Plane logs                                  |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | - EKS managed Autoscaling groups as worker nodes                            |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| [ECK (Elastic                                                                                                                                               | Based on Kubernetes operator pattern this operator orchestrates             |
| Operator)](https://www.elastic.co/blog/introducing-elastic-cloud-on-kubernetes-the-elasticsearch-operator-and-beyond?elektra=products&storm=sub1)           | Elasticsearch, Kibana, Beats deployments on Kubernetes. CRDs installed by   |
|                                                                                                                                                             | ECK can be listed as:                                                       |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | bash➜ \~ kubectl get crd \| grep elastic NAME CREATED AT                    |
|                                                                                                                                                             | agents.agent.k8s.elastic.co 2022-05-13T10:46:40Z                            |
|                                                                                                                                                             | apmservers.apm.k8s.elastic.co 2022-05-13T10:46:40Z                          |
|                                                                                                                                                             | beats.beat.k8s.elastic.co 2022-05-13T10:46:40Z                              |
|                                                                                                                                                             | elasticmapsservers.maps.k8s.elastic.co 2022-05-13T10:46:40Z                 |
|                                                                                                                                                             | elasticsearches.elasticsearch.k8s.elastic.co 2022-05-13T10:46:40Z           |
|                                                                                                                                                             | enterprisesearches.enterprisesearch.k8s.elastic.co 2022-05-13T10:46:41Z     |
|                                                                                                                                                             | kibanas.kibana.k8s.elastic.co 2022-05-13T10:46:41Z                          |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | Elastic Operator runs as a pod in the `elastic-system` namespace and whose  |
|                                                                                                                                                             | logs can be viewed as                                                       |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | bash➜ \~ kubectl get pods -n elastic-system NAME READY STATUS RESTARTS AGE  |
|                                                                                                                                                             | elastic-operator-0 1/1 Running 0 35d ➜ \~ kubectl get pods -n               |
|                                                                                                                                                             | elastic-system                                                              |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| [Elasticsearch Data Nodes](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-node.html)                                               | Elasticsearch node that has the `data` role. Data nodes hold data and       |
|                                                                                                                                                             | perform data related operations such as CRUD, search, and aggregations.\    |
|                                                                                                                                                             | We run dedicated EKS Managed Groups for Elasticsearch Data nodes in an      |
|                                                                                                                                                             | Availability Zone. If a cluster is configured to run in multiple AZs then a |
|                                                                                                                                                             | separate node group for data nodes in each AZ is created. These Managed     |
|                                                                                                                                                             | Node Groups are named as                                                    |
|                                                                                                                                                             | `eks-prod-data-NG-1a-*, eks-prod-data-NG-1b-*, eks-prod-data-NG-1c-*`       |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | In Kubernetes, these Data Node process/pods are deployed as statefulsets in |
|                                                                                                                                                             | a namespace named like `josh-cms-prod-es-eck` where `josh-cms` in the ECK   |
|                                                                                                                                                             | cluster\                                                                    |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | bash➜ \~ kubectl get statefulsets -n josh-cms-prod-es-eck \| grep es-data   |
|                                                                                                                                                             | NAME READY AGE elasticsearch-es-data-zone-a 2/2 35d                         |
|                                                                                                                                                             | elasticsearch-es-data-zone-b 2/2 35d elasticsearch-es-data-zone-c 1/1 35d   |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| [Elasticsearch Master Nodes](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-node.html)                                             | Master nodes are in charge of cluster-wide settings and changes -- deleting |
|                                                                                                                                                             | or creating indices and fields, adding or removing nodes and allocating     |
|                                                                                                                                                             | shards to nodes. Each cluster has a single master node that is elected from |
|                                                                                                                                                             | the master eligible nodes using a distributed consensus algorithm and is    |
|                                                                                                                                                             | reelected if the current master node fails.                                 |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | We run dedicated EKS Managed Groups for Elasticsearch Master nodes in an    |
|                                                                                                                                                             | Availability Zone. If a cluster is configured to run in multiple AZs then a |
|                                                                                                                                                             | separate node group for Master nodes in each AZ is created. These Managed   |
|                                                                                                                                                             | Node Groups are named as                                                    |
|                                                                                                                                                             | `eks-prod-master-NG-1a-*, eks-prod-master-NG-1b-*, eks-prod-master-NG-1c-*` |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | In Kubernetes, these Data Node process/pods are deployed as statefulsets in |
|                                                                                                                                                             | a namespace named like `josh-cms-prod-es-eck` where `josh-cms` in the ECK   |
|                                                                                                                                                             | cluster\                                                                    |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | bash➜ \~ kubectl get statefulsets -n josh-cms-prod-es-eck NAME READY AGE    |
|                                                                                                                                                             | elasticsearch-es-master-zone-a 3/3 35d elasticsearch-es-master-zone-b 2/2   |
|                                                                                                                                                             | 35d elasticsearch-es-master-zone-c 2/2 35d                                  |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| Elasticsearch System Nodes                                                                                                                                  | Dedicated Node Group which runs the ECK Operator pod runs. The node group   |
|                                                                                                                                                             | spans two AZs and is named as `eks-ES-system-NG-*`                          |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| [Kibana](https://www.elastic.co/guide/en/kibana/current/introduction.html)                                                                                  | Kibana provides user interface that lets you visualize your Elasticsearch   |
|                                                                                                                                                             | data and navigate, administer and monitor the Elastic Stack. Kibana         |
|                                                                                                                                                             | process/pods are deployed as deployment in a namespace named like           |
|                                                                                                                                                             | `josh-cms-prod-es-eck` where `josh-cms` in the ECK cluster                  |
|                                                                                                                                                             |                                                                             |
|                                                                                                                                                             | bash➜ \~ kubectl get deployments -n josh-cms-prod-es-eck \| grep kibana     |
|                                                                                                                                                             | kibana-kb 2/2 2 2 35d                                                       |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| Metricbeat                                                                                                                                                  |                                                                             |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| Prometheus Operator                                                                                                                                         |                                                                             |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| Load Balancer Service                                                                                                                                       |                                                                             |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| Name records                                                                                                                                                |                                                                             |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+

## Support Contacts

------------------------------------------------------------------------

+-------------------+-------------------------+----------------+------------------+
| **Team**          | **Responsibilities**    | **Support      | **Contact Info** |
|                   |                         | Scope/Level**  |                  |
+-------------------+-------------------------+----------------+------------------+
| Elasticsearch     | - Escalations for       |                |                  |
| Platinum/Standard |   problems(performance, |                |                  |
| Support           |   availability,         |                |                  |
|                   |   reliability) with     |                |                  |
|                   |   Elasticsearch,        |                |                  |
|                   |   Kibana, ECK Operator  |                |                  |
|                   |                         |                |                  |
|                   | - Architecture Guidance |                |                  |
|                   |   and Recommendations   |                |                  |
|                   |                         |                |                  |
|                   | - RCA for Elastic       |                |                  |
|                   |   problems              |                |                  |
+-------------------+-------------------------+----------------+------------------+
| AWS Premium       | - EKS cluster           |                |                  |
| Support           |                         |                |                  |
+-------------------+-------------------------+----------------+------------------+
|                   | G7CR                    |                |                  |
+-------------------+-------------------------+----------------+------------------+

 

## ECK Cluster Inventory

------------------------------------------------------------------------

## Cluster Deployment and Configuration Information

------------------------------------------------------------------------

## Monitoring

------------------------------------------------------------------------

## Alerting

------------------------------------------------------------------------

## KnowledgeBase Articles

------------------------------------------------------------------------
