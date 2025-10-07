**Overview**:- The Prometheus Operator provides
[Kubernetes](https://kubernetes.io/) native deployment and management of
[Prometheus](https://prometheus.io/) and related monitoring components.
This this project is to simplify and automate the configuration of a
Prometheus based monitoring stack for Kubernetes clusters.

### Prometheus Operator:-

In simple words, [Prometheus
Operator](https://prometheus-operator.dev/) is a fully automated way of
deploying (like any other standard Kubernetes Deployment object)
Prometheus server, Alertmanager and all the related secrets, configmap
etc; that will help to [set up Prometheus
monitoring](https://www.infracloud.io/observability-consulting/) ecosystem
and instantiate Kubernetes cluster monitoring in just a few minutes.

Once deployed, Prometheus Operator provides the following features:

**Automation:** Easily launch a Prometheus instance for your Kubernetes
namespace, a specific application, or a team.

**Service discovery:** Automatically discover the targets to be
monitored using familiar Kubernetes label queries; without a need to
learn a Prometheus specific configuration language.

**Easy Configuration:** Manage the configuration of the essential
resources of Prometheus like versions, persistence, retention policies,
and replicas from a Kubernetes resource.

## Prerequisites:-

Prometheus Operator `>=0.39.0`

Kubernetes cluster `>=1.16.0`.

It is highly recommended to use the latest version

## CustomResourceDefinitions

A core feature of the Prometheus Operator is to monitor the Kubernetes
API server for changes to specific objects and ensure that the current
Prometheus deployments match these objects. The Operator acts on the
following [custom resource definitions
(CRDs)](https://kubernetes.io/docs/tasks/access-kubernetes-api/extend-api-custom-resource-definitions/):

- `Prometheus`, which defines a desired Prometheus deployment.

- `Alertmanager`, which defines a desired Alertmanager deployment.

- `ThanosRuler`, which defines a desired Thanos Ruler deployment.

- `ServiceMonitor`, which declaratively specifies how groups of
  Kubernetes services should be monitored. The Operator automatically
  generates Prometheus scrape configuration based on the current state
  of the objects in the API server.

- `PodMonitor`, which declaratively specifies how group of pods should
  be monitored. The Operator automatically generates Prometheus scrape
  configuration based on the current state of the objects in the API
  server.

- `Probe`, which declaratively specifies how groups of ingresses or
  static targets should be monitored. The Operator automatically
  generates Prometheus scrape configuration based on the definition.

- `PrometheusRule`, which defines a desired set of Prometheus alerting
  and/or recording rules. The Operator generates a rule file, which can
  be used by Prometheus instances.

- `AlertmanagerConfig`, which declaratively specifies subsections of the
  Alertmanager configuration, allowing routing of alerts to custom
  receivers, and setting inhibit rules.

Installation Steps:-

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts `

`helm repo update `

`helm install prometheus prometheus-community/kube-prometheus-stack`
