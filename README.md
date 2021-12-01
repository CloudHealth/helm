<!-- Copyright 2021 VMware, Inc. -->
<!-- SPDX-License-Identifier: Apache-2.0 -->
# CloudHealth Kubernetes Collector Agent Helm Chart

[CloudHealth](https://www.cloudhealthtech.com/) is a Cloud Management Solution. CloudHealth provides long-term, trended visibility into container resource utilization by service and team. The module helps you discover which services are consuming the most resources and identify opportunities for optimization.

To use this functionality, use this helm chart to deploy the collector agent into each Kubernetes cluster in your environment.

## TL;DR

```console
$ helm repo add cloudhealth https://github.com/CloudHealth/helm
$ helm install my-release --set apiToken=<Unique Customer API Token>,clusterName=<Cluster Name> cloudhealth-collector
```

## Introduction

This chart bootstraps a CloudHealth Collector Agent deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.12+
- Helm 3.1.0

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm repo add cloudhealth https://github.com/CloudHealth/helm
$ helm install my-release --set apiToken=<Unique Customer API Token>,clusterName=<Cluster Name> cloudhealth-collector
```

These commands deploy the CloudHealth Collector on the Kubernetes cluster in the default configuration. The [Parameters](#parameters) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release
```
The command removes all the Kubernetes components associated with the chart and deletes the release. Remove also the chart using `--purge` option:

```console
$ helm delete --purge my-release
```

## Parameters

### Required parameters

| Name                     | Description                                                                             | Value           |
| ------------------------ | --------------------------------------------------------------------------------------- | --------------- |
| `apiToken`            | Unique Customer API Token provided by CloudHealth                                                             | `<change-me>`            |
| `clusterName`           | Name of the cluster to be shown on the CloudHealth UI                                      | `your-cluster-name`            |


### Other parameters

| Name                        | Description                                                                                  | Value                 |
| --------------------------- | -------------------------------------------------------------------------------------------- | --------------------- |
| `image.repository`          | CloudHealth Collector image repository                                                            | `cloudhealth/container-collector`      |
| `image.tag`                 | CloudHealth Collector image tag (immutable tags are recommended)                                  | `latest` |
| `image.pullPolicy`          | CloudHealth Collector image pull policy                                                           | `Always`        |
| `image.pullSecrets`         | CloudHealth Collector image pull secrets                                                          | `[]`                  |
| `replicaCount`                          | Number of CloudHealth Collector replicas to deploy                                             | `1`|
| `resources.limits.cpu`                      | The CPU limits for CloudHealth Collector containers                                      | `1000m`            |
| `resources.requests.cpu`                    | The requested CPU for CloudHealth Collector containers                                   | `500m`            |
| `resources.limits.memory`                      | The Memory limits for CloudHealth Collector containers                                      | `1024Mi`            |
| `resources.requests.memory`                    | The requested Memory for CloudHealth Collector containers                                   | `512Mi`            |
| `nameOverride`       | String to override common.names.fullname                                          | `""`            |
| `fullnameOverride`       | String to fully override common.names.fullname                                          | `""`            |
| `secretName`       | Kubernetes secret name created to store CloudHealth API Token & Secret                                         | `cloudhealth-config`            |
| `service.type`                  | CloudHealth Collector UI Service Type                                                                                                 | `ClusterIP`              |
| `service.port`                  | CloudHealth Collector UI Service Type                                                                                                 | `80`              |
| `podAnnotations`                        | Additional pod annotations                                                                | `{}`            |
| `podSecurityContext`            | Enable security context for CloudHealth Collector pods                                         | `{}`          |
| `securityContext`            | Enable security context for CloudHealth Collector                                         | `{}`          |
| `affinity`                              | Affinity for pod assignment                                                               | `{}`            |
| `nodeSelector`                          | Node labels for pod assignment                                                            | `{}`            |
| `tolerations`                           | Tolerations for pod assignment                                                            | `[]`            |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install my-release --set apiToken=sample_token,clusterName=mega-cluster cloudhealth-collector
```

The above command sets the CloudHealth Collector apiToken to `sample_token` and sets the cluster name to `mega-cluster`.

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
$ helm install my-release -f values.yaml cloudhealth-collector
```

> **Tip**: You can use the default [values.yaml](values.yaml)

## Troubleshooting

Find more information about how to deal with common errors related to CloudHealth’s Helm charts in [this troubleshooting guide](https://docs.bitnami.com/general/how-to/troubleshoot-helm-chart-issues).

**Useful links**

- https://docs.bitnami.com/tutorials/resolve-helm2-helm3-post-migration-issues/
- https://helm.sh/docs/topics/v2_v3_migration/
- https://helm.sh/blog/migrate-from-helm-v2-to-helm-v3/


