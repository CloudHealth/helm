<!-- Copyright 2023 VMware, Inc. -->
<!-- SPDX-License-Identifier: Apache-2.0 -->
# CloudHealth Kubernetes Collector Agent Helm Chart

[CloudHealth](https://www.cloudhealthtech.com/) is a multi-cloud cost optimization solution that enables businesses to simplify cloud financial management, streamline operations, and strengthen security and compliance.

To avail this functionality, use this helm chart to deploy the collector agent into each Kubernetes cluster in your environment.

## TL;DR

```console
$ helm repo add cloudhealth https://cloudhealth.github.io/helm/
$ helm install cloudhealth-collector --set apiToken=<Unique Customer API Token>,clusterName=<Cluster Name>,chtRegion=<Cloudhealth Region> cloudhealth/cloudhealth-collector
```

## Getting Started

Use the helm chart to deploy the CloudHealth Collector into each [Kubernetes](http://kubernetes.io) cluster in your environment.

## Prerequisites

- Kubernetes 1.12+
- Helm 3.0+
- CloudHealth API Token

## Installing the Chart

To install the chart with the release name `cloudhealth-collector`, run the following command:

```console
$ helm repo add cloudhealth https://cloudhealth.github.io/helm/
$ helm install cloudhealth-collector --set apiToken=<Unique Customer API Token>,clusterName=<Cluster Name>,chtRegion=<Cloudhealth Region> cloudhealth/cloudhealth-collector
```

To install the chart with the release name `cloudhealth-collector` in a particular namespace `<target_namespace>`, run the following commands:

```console
$ helm repo add cloudhealth https://cloudhealth.github.io/helm/
$ helm install cloudhealth-collector -n <target_namespace> --set apiToken=<Unique Customer API Token>,clusterName=<Cluster Name>,chtRegion=<Cloudhealth Region> cloudhealth/cloudhealth-collector
```

The `apiToken` is required for `cloudhealth-collector` to work and should be either set while running helm install command as in the example above or in a secret object with the following data structure:
```yaml
data:
  apiToken:  "PGNoYW5nZS1tZT4="
```

These commands deploy the CloudHealth Collector on the Kubernetes cluster in the default configuration. The [Parameters](#parameters) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Updating the Chart

To update an existing release to the latest version of the chart, run the following command:
```
$ helm upgrade cloudhealth-collector cloudhealth/cloudhealth-collector
```

## Uninstalling the Chart

To uninstall the `cloudhealth-collector` deployment and remove the CloudHealth Helm Chart repository, run the following commands:

```console
$ helm uninstall cloudhealth-collector
$ helm repo remove cloudhealth
```

## Parameters

### Required parameters

| Name          | Description                                           | Value    |
|---------------|-------------------------------------------------------| -------- |
| `clusterName` | Name of the cluster to be shown on the CloudHealth UI | `""`     |


### Other parameters

| Name                        | Description                                                                                       | Value                             |
|-----------------------------|---------------------------------------------------------------------------------------------------|-----------------------------------|
| `apiToken`                  | Unique Customer API Token provided by CloudHealth                                                 | `""`                              |
| `chtRegion`                 | CloudHealth Region provided by CloudHealth (CloudHealth region where customer is onboarded)       | `us-east-1`                       |
| `image.repository`          | CloudHealth Collector image repository                                                            | `cloudhealth/container-collector` |
| `image.tag`                 | CloudHealth Collector image tag                                                                   | `1398`                            |
| `image.pullPolicy`          | CloudHealth Collector image pull policy                                                           | `IfNotPresent`                    |
| `image.pullSecrets`         | CloudHealth Collector image pull secrets                                                          | `[]`                              |
| `resources.limits.cpu`      | The CPU limits for CloudHealth Collector containers                                               | `1000m`                           |
| `resources.requests.cpu`    | The requested CPU for CloudHealth Collector containers                                            | `500m`                            |
| `resources.limits.memory`   | The Memory limits for CloudHealth Collector containers                                            | `1024Mi`                          |
| `resources.requests.memory` | The requested Memory for CloudHealth Collector containers                                         | `512Mi`                           |
| `nameOverride`              | String to override common.names.fullname                                                          | `""`                              |
| `fullnameOverride`          | String to fully override common.names.fullname                                                    | `""`                              |
| `secretName`                | Kubernetes secret name created to store CloudHealth API Token & Secret                            | `cloudhealth-config`              |
| `podAnnotations`            | Additional pod annotations                                                                        | `{}`                              |
| `podSecurityContext`        | Enable security context for CloudHealth Collector pods                                            | `{}`                              |
| `securityContext`           | Enable security context for CloudHealth Collector                                                 | `{}`                              |
| `affinity`                  | Affinity for pod assignment                                                                       | `{}`                              |
| `nodeSelector`              | Node labels for pod assignment                                                                    | `{}`                              |
| `tolerations`               | Tolerations for pod assignment                                                                    | `[]`                              |
| `customLabels`              | Custom labels to add to all resources created by this chart                                       | `{}`                              |
| `customEnvVars`             | Extra environment variable to add to pod created by this chart (has to be a `name`, `value` pair) | `[]`                              |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example, the following command sets the CloudHealth Collector API Token to `sample_token` and sets the cluster name to `mega-cluster`.

```console
$ helm install cloudhealth-collector --set apiToken=sample_token,clusterName=mega-cluster,chtRegion=us-east-1 cloudhealth/cloudhealth-collector
```

Example with `customEnvVars`
```console
$ helm install cloudhealth-collector --set apiToken=sample_token,clusterName=mega-cluster --set "customEnvVars[0].name=ENV4" --set "customEnvVars[0].value=VALUE4" cloudhealth/cloudhealth-collector
```

You can also use YAML file to specify the parameters while installing the chart. For example, the following command indicates that the file `values.yaml` should be used to set the parameters:

```console
$ helm install cloudhealth-collector -f values.yaml cloudhealth/cloudhealth-collector
```

> **Tip**: You can use the default [values.yaml](charts/cloudhealth-collector/values.yaml)

## Troubleshooting

Find more information about how to deal with common errors related to CloudHealth’s Helm charts in [this troubleshooting guide](https://docs.bitnami.com/general/how-to/troubleshoot-helm-chart-issues).

**Useful links**

- https://help.cloudhealthtech.com/
- https://docs.bitnami.com/tutorials/resolve-helm2-helm3-post-migration-issues/
- https://helm.sh/docs/topics/v2_v3_migration/
- https://helm.sh/blog/migrate-from-helm-v2-to-helm-v3/
