# ckeeper

A Helm chart for the CKeeper of the GLA e-Navigation Service Architecture

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: latest](https://img.shields.io/badge/AppVersion-latest-informational?style=flat-square)

## The e-Navigation CKeeper Service

In the GLA e-Navigation Service Architecture an additional microservice is
required to interface with the MCP. The **Certificate Keeper** microservice has
been designed explicitly for that purpose. It interfaces with the MCP MIR
securely using the TLS/SSL protocol, and is able to generate a new MCP X.509
certificate for each of the architecture elements, including the services, the
users and of course the advertised VAtoN. The generated certificates along with
their public/private key pairs are cached in a local microservice database, so
that it is easier to generate signatures for the transmitted messages, as well
as verify incoming messages based on the provided signatures. The microservice
has an additional feature, where it can be used as a stand-alone application on
the client side, in order to provide an easier and more robust way to verify the
messages originating from the CSSA, especially in cases of intermittent
connectivity.

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
| env[0].valueFrom.configMapKeyRef.name | string | `"ckeeper-config"` |  |
| env[1].name | string | `"ENAV_CLOUD_CONFIG_BRANCH"` |  |
| env[1].valueFrom.configMapKeyRef.key | string | `"config_branch"` |  |
| env[1].valueFrom.configMapKeyRef.name | string | `"ckeeper-config"` |  |
| env[2].name | string | `"ENAV_CLOUD_CONFIG_USERNAME"` |  |
| env[2].valueFrom.secretKeyRef.key | string | `"config_username"` |  |
| env[2].valueFrom.secretKeyRef.name | string | `"ckeeper-secrets"` |  |
| env[3].name | string | `"ENAV_CLOUD_CONFIG_PASSWORD"` |  |
| env[3].valueFrom.secretKeyRef.key | string | `"config_password"` |  |
| env[3].valueFrom.secretKeyRef.name | string | `"ckeeper-secrets"` |  |
| fullnameOverride | string | `""` |  |
| global.ckeeper.keystore | string | `""` |  |
| global.ckeeper.truststore | string | `""` |  |
| global.enav_service.cloud_config.branch | string | `"master"` |  |
| global.enav_service.cloud_config.password | string | `"enav_config_password"` |  |
| global.enav_service.cloud_config.url | string | `"http://enav-eureka.enav.svc.k8s:8761/config/"` |  |
| global.enav_service.cloud_config.username | string | `"enav_config_user"` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"ghcr.io/gla-rad/enav-ckeeper"` |  |
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
| service.port | int | `8764` |  |
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
| volumes[2].projected.sources[0].secret.name | string | `"ckeeper-secrets"` |  |
| volumes[2].projected.sources[1].secret.items[0].key | string | `"truststore"` |  |
| volumes[2].projected.sources[1].secret.items[0].path | string | `"truststore.jks"` |  |
| volumes[2].projected.sources[1].secret.name | string | `"ckeeper-secrets"` |  |
| waitForServices[0].serviceName | string | `"eureka"` |  |
| waitForServices[0].servicePort | int | `8761` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.13.1](https://github.com/norwoodj/helm-docs/releases/v1.13.1)