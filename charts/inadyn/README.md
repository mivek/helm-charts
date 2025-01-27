# inadyn

A Helm chart deploying Inadyn as a cronjob for Kubernetes

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.12.0](https://img.shields.io/badge/AppVersion-2.12.0-informational?style=flat-square)

## Installation

Add the Helm repository
```bash
helm repo add mivek https://mivek.github.io/helm-charts
helm update
```

To install the chart with the release name `my-release`:
```bash
helm install my-release mivek/inadyn -n namespace
```

This will deploy a cronjob.

## Configuration

The following table lists the configurable parameters of the Inadyn chart and their default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| cache | object | `{"accessMode":"ReadWriteOnce","enabled":true,"size":"50Mi","storageClass":""}` | Cache volume for Inadyn. If enabled a PVC will be created. |
| config | string | `""` | The configuration for Inadyn. |
| image.pullPolicy | string | `"IfNotPresent"` | This sets the pull policy for images. |
| image.repository | string | `"troglobit/inadyn"` | The inadyn image to use. |
| image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| imagePullSecrets | list | `[]` | This is for the secretes for pulling an image from a private repository more information can be found here: https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/ |
| restartPolicy | string | `"OnFailure"` | The restart policy for the cronjob. |
| schedule | string | `"*/5 * * * *"` | Cron schedule for Inadyn. |
| secrets | object | `{}` | This creates a secret fpr Inadyn. The secrets are then usable in the container as environment variables. |
| timeZone | string | `"UTC"` | The timezone for the cron schedule. |

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| mivek |  | <https://github.com/mivek> |