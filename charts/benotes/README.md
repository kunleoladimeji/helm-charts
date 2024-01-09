# benotes

A Helm chart for Benotes application

## TL;DR;

```console
helm repo add kunleoladimeji https://charts.olakunleoladimeji.com/helm-charts
helm repo update
helm install my-release kunleoladimeji/benotes
```

## Introduction

<INTRODUCTION>

This chart bootstraps the [Benotes](<https://benotes.org/>) on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.19+

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm repo add kunleoladimeji https://charts.olakunleoladimeji.com/helm-charts
helm repo update
helm install my-release kunleoladimeji/benotes
```

These commands deploy Benotes on the Kubernetes cluster in the default configuration. The [Values](#values) section lists the values that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall the `my-release` deployment:

```console
helm uninstall my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Affinity settings for pod assignment |
| appKey | string | `"change-me"` |  |
| autoscaling.enabled | bool | `false` | Enable Horizontal POD autoscaling  |
| autoscaling.maxReplicas | int | `100` | Maximum number of replicas |
| autoscaling.minReplicas | int | `1` | Minimum number of replicas |
| autoscaling.targetCPUUtilizationPercentage | int | `80` | Target CPU utilization percentage |
| autoscaling.targetMemoryUtilizationPercentage | int | `80` | Target Memory utilization percentage |
| extraEnv | list | `[]` | additional environment variables to be added to the pods |
| fullnameOverride | string | `""` | String to fully override `"benotes.fullname"` |
| image.pullPolicy | string | `"Always"` | image pull policy |
| image.registry | string | `"docker.io"` | image registry |
| image.repository | string | `"fr0tt/benotes"` | image repository |
| image.tag | string | `"2.8.2"` | Overrides the image tag |
| imagePullSecrets | list | `[]` | If defined, uses a Secret to pull an image from a private Docker registry or repository. |
| ingress.annotations | object | `{}` | Additional annotations for the Ingress resource |
| ingress.className | string | `""` | IngressClass that will be be used to implement the Ingress |
| ingress.enabled | bool | `false` | Enable ingress record generation |
| ingress.hosts | list | see [values.yaml](./values.yaml) | An array with hosts and paths |
| ingress.tls | list | `[]` | An array with the tls configuration |
| jwtSecret | string | `"change-me"` |  |
| mail.enabled | bool | `false` |  |
| mail.fromAddress | string | `nil` |  |
| mail.host | string | `nil` |  |
| mail.password | string | `nil` |  |
| mail.username | string | `nil` |  |
| mysql.enabled | bool | `false` |  |
| nameOverride | string | `""` | Provide a name in place of `benotes` |
| nodeSelector | object | `{}` | Node labels for pod assignment |
| persistence.accessModes | list | `["ReadWriteOnce"]` | the desired access modes the volume should have. |
| persistence.annotations | object | `{}` | Annotations to be added to the PersistentVolumeClaim |
| persistence.enabled | bool | `false` | use a PVC to persist data |
| persistence.existingClaim | string | `""` | provide an existing PersistentVolumeClaim |
| persistence.path | string | `"/var/www/storage"` |  |
| persistence.size | string | `"1Gi"` |  |
| persistence.storageClassName | string | `""` | Name of the StorageClass required by the claim. |
| podAnnotations | object | `{}` | Annotations to be added to the pods |
| podSecurityContext | object | `{}` | pod-level security context |
| postgresql.enabled | bool | `false` |  |
| replicaCount | int | `1` | Number of replicas |
| resources | object | `{}` | Resource limits and requests for the controller pods. |
| revisionHistoryLimit | int | `10` | The number of old ReplicaSets to retain |
| securityContext | object | `{}` | container-level security context |
| service.port | int | `80` | Kubernetes port where service is exposed |
| service.type | string | `"ClusterIP"` | Kubernetes service type |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| sqlite.dbPath | string | `"database.sqlite"` |  |
| sqlite.enabled | bool | `true` |  |
| tolerations | list | `[]` | Toleration labels for pod assignment |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml christianknell/<CHARTNAME>
```

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.12.0](https://github.com/norwoodj/helm-docs/releases/v1.12.0)