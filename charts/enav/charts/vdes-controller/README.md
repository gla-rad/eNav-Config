# vdes-controller

A Helm chart for the Message-Broker GLA e-Navigation Service Architecture

![Version: 0.0.2](https://img.shields.io/badge/Version-0.0.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: latest](https://img.shields.io/badge/AppVersion-latest-informational?style=flat-square)

## The e-Navigation VDES Controller Service

The GLA identified the provision of VAtoN as one of the top priority use-cases
for their future e-Navigation applications. The use-case requirements stated
that the transmission must be performed over AIS/VDES, therefore the
architecture should include a component that provides this capability.
Consequently, the **VDES Controller** microservice was introduced, which is
capable of interfacing with VDES modules like the CML Microcircuits VDES1000,
using a set of predefined UDP/IP ports. The application is therefore able to
transmit messages using the TSA/VDM (Transmit Slot Assignment/VHF Data-link
Message) and the BBM (Broadcast Binary Message) sentence protocols. **VDES
Controller** can receive the current VAtoN information by either polling or
subscribing to the **AtoN Service** microservice, and translates it to the
appropriate transmission format. For testing purposes, the service is also able
to send AIS messages using the Ettus E320 software-defined radio USRP platform
in a similar manner.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| env[0].name | string | `"ENAV_CLOUD_CONFIG_URI"` |  |
| env[0].valueFrom.configMapKeyRef.key | string | `"config_endpoint"` |  |
| env[0].valueFrom.configMapKeyRef.name | string | `"vdes-controller-config"` |  |
| env[1].name | string | `"ENAV_CLOUD_CONFIG_BRANCH"` |  |
| env[1].valueFrom.configMapKeyRef.key | string | `"config_branch"` |  |
| env[1].valueFrom.configMapKeyRef.name | string | `"vdes-controller-config"` |  |
| env[2].name | string | `"ENAV_CLOUD_CONFIG_USERNAME"` |  |
| env[2].valueFrom.secretKeyRef.key | string | `"config_username"` |  |
| env[2].valueFrom.secretKeyRef.name | string | `"vdes-controller-secrets"` |  |
| env[3].name | string | `"ENAV_CLOUD_CONFIG_PASSWORD"` |  |
| env[3].valueFrom.secretKeyRef.key | string | `"config_password"` |  |
| env[3].valueFrom.secretKeyRef.name | string | `"vdes-controller-secrets"` |  |
| fullnameOverride | string | `""` |  |
| global.enav_service.cloud_config.branch | string | `"master"` |  |
| global.enav_service.cloud_config.password | string | `"enav_config_password"` |  |
| global.enav_service.cloud_config.url | string | `"http://enav-eureka.enav.svc.k8s:8761/config/"` |  |
| global.enav_service.cloud_config.username | string | `"enav_config_user"` |  |
| global.vdes_controller.keystore | string | `""` |  |
| global.vdes_controller.truststore | string | `""` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"ghcr.io/gla-rad/enav-vdes-controller"` |  |
| image.tag | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `""` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls | list | `[]` |  |
| livenessProbe.httpGet.path | string | `"/actuator/health/liveness"` |  |
| livenessProbe.httpGet.port | string | `"http"` |  |
| nameOverride | string | `""` |  |
| nodeSelector."kubernetes.io/os" | string | `"linux"` |  |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| readinessProbe.httpGet.path | string | `"/actuator/health/readiness"` |  |
| readinessProbe.httpGet.port | string | `"http"` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `8762` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.automount | bool | `true` |  |
| serviceAccount.create | bool | `false` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` |  |
| volumeMounts[0].mountPath | string | `"/tmp"` |  |
| volumeMounts[0].name | string | `"tmp-volume"` |  |
| volumeMounts[1].mountPath | string | `"/var/log"` |  |
| volumeMounts[1].name | string | `"log-volume"` |  |
| volumeMounts[2].mountPath | string | `"/ssl"` |  |
| volumeMounts[2].name | string | `"ssl-volume"` |  |
| volumeMounts[2].readOnly | bool | `true` |  |
| volumes[0].emptyDir | object | `{}` |  |
| volumes[0].name | string | `"tmp-volume"` |  |
| volumes[1].emptyDir | object | `{}` |  |
| volumes[1].name | string | `"log-volume"` |  |
| volumes[2].name | string | `"ssl-volume"` |  |
| volumes[2].projected.sources[0].secret.items[0].key | string | `"keystore"` |  |
| volumes[2].projected.sources[0].secret.items[0].path | string | `"keystore.jks"` |  |
| volumes[2].projected.sources[0].secret.name | string | `"vdes-controller-secrets"` |  |
| volumes[2].projected.sources[1].secret.items[0].key | string | `"truststore"` |  |
| volumes[2].projected.sources[1].secret.items[0].path | string | `"truststore.jks"` |  |
| volumes[2].projected.sources[1].secret.name | string | `"vdes-controller-secrets"` |  |
| waitForServices[0].serviceName | string | `"eureka"` |  |
| waitForServices[0].servicePort | int | `8761` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.13.1](https://github.com/norwoodj/helm-docs/releases/v1.13.1)