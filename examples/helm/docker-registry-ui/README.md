# docker-registry-ui

[docker-registry-ui](https://joxit.dev/docker-registry-ui/) is the simplest and most complete UI for your private registry!


## Introduction

This chart bootstraps a [docker-registry-ui](https://joxit.dev/docker-registry-ui/) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites


## Installing the Chart

To install the chart with the release name `my-release` and registry at `https://registry.example.com`:

```bash
$ helm update --install my-release \
  --set registry.url=https://registry.example.com \
    .
```

The command deploys docker-registry-ui on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the Redmine chart and their default values.

|            Parameter              |              Description                 |                          Default                        | 
| --------------------------------- | ---------------------------------------- | ------------------------------------------------------- |
| `ui.title`                        | Title of the managed repository          | `Docker registry UI`                                    |
| `ui.delete_images`                | Allow to delete image from the front-end | `false`                                                 |
| `ui.proxy`                        | The UI service act as a proxy of the registry | `true`                                             |
| `ui.replicaCount`                 | Number of replicas to start              | `1`                                                     |
| `ui.image.registry`               | registry to pull the docker-registry-ui image from | `docker.io`                                   |
| `ui.image.repository`             | docker-registry-ui image name            | `joxit/docker-registry-ui`                              |
| `ui.image.tag`                    | docker-registry-ui image tag             | `2.0`          |
| `ui.image.pullPolicy`             | docker-registry-ui image pull policy     | `Always`                                                |
| `ui.probe.liveness`               | Ask kubernetes to check the service port for liveness | `true`                                     |
| `ui.probe.readyness `             | Ask kubernetes to check the service port for readyness | `true`                                    |
| `ui.service.type`                 | Desired service type                     | `ClusterIP`                                             |
| `ui.service.port`                 | Service exposed port                     | `80`                                                    |
| `ui.ingress.enabled`              | Create an ingress for docker-regstry-ui  | `false`                                                 |
| `registry.external` 		    | Use an already available registry        | `false`						 |
| `registry.url` 		    | URL of the existing registry (Change )            | `https://example.com:5000`				 |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
$ helm upgrade --install my-release \
  --set registry.url=http://registry.example.com:5000 \
    .
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```bash
$ helm upgrade --install my-release -f values.yaml .
```

> **Tip**: You can use the default [values.yaml](values.yaml)

