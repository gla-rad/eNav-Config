# eureka

A Helm chart for the Eureka Service of the GLA e-Navigation Service Architecture

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: latest](https://img.shields.io/badge/AppVersion-latest-informational?style=flat-square)

## The e-Navigation Eureka Service

This is the internal component the handles the service discovery and facilitates
the microservice inter-communication. It should not be confused with a MCP MSR
component, as it is only focused on the discoverability of the internal
e-Navigation Service Architecture microservices. It is based on the
[Netflix Eureka](https://github.com/Netflix/eureka) service implementation which
allows the registered microservices to be contacted via a simple name identifier.
It removes the requirement for microservices to be aware of each other’s
addresses (IP, URL) beforehand, and also supports the system scaling operation
by allowing multiple instances of each microservice to be used according to a
selected load-balancing strategy.

The current implementation is also enriched with additional functionality that
supports a
[Springboot Admin](http://docs.spring-boot-admin.com/current/index.html)
server for monitoring, as well as a
[Spring Cloud Config](https://spring.io/projects/spring-cloud-config) server
that provides support for externalized configuration in a distributed system.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| env[0].name | string | `"ENAV_CONFIG_REPO_URL"` |  |
| env[0].valueFrom.configMapKeyRef.key | string | `"config_repo"` |  |
| env[0].valueFrom.configMapKeyRef.name | string | `"eureka-config"` |  |
| env[1].name | string | `"ENAV_CONFIG_REPO_BRANCH"` |  |
| env[1].valueFrom.configMapKeyRef.key | string | `"config_branch"` |  |
| env[1].valueFrom.configMapKeyRef.name | string | `"eureka-config"` |  |
| env[2].name | string | `"ENAV_CONFIG_REPO_USERNAME"` |  |
| env[2].valueFrom.secretKeyRef.key | string | `"ENAV_CONFIG_REPO_USERNAME"` |  |
| env[2].valueFrom.secretKeyRef.name | string | `"eureka-secrets"` |  |
| env[3].name | string | `"ENAV_CONFIG_REPO_PASSWORD"` |  |
| env[3].valueFrom.secretKeyRef.key | string | `"ENAV_CONFIG_REPO_PASSWORD"` |  |
| env[3].valueFrom.secretKeyRef.name | string | `"eureka-secrets"` |  |
| env[4].name | string | `"ENAV_CLOUD_CONFIG_USERNAME"` |  |
| env[4].valueFrom.secretKeyRef.key | string | `"ENAV_CLOUD_CONFIG_USERNAME"` |  |
| env[4].valueFrom.secretKeyRef.name | string | `"service-secrets"` |  |
| env[5].name | string | `"ENAV_CLOUD_CONFIG_PASSWORD"` |  |
| env[5].valueFrom.secretKeyRef.key | string | `"ENAV_CLOUD_CONFIG_PASSWORD"` |  |
| env[5].valueFrom.secretKeyRef.name | string | `"service-secrets"` |  |
| env[6].name | string | `"ENAV_CONFIG_ENCRYPTION_KEY"` |  |
| env[6].valueFrom.secretKeyRef.key | string | `"ENAV_CONFIG_ENCRYPTION_KEY"` |  |
| env[6].valueFrom.secretKeyRef.name | string | `"eureka-secrets"` |  |
| fullnameOverride | string | `""` |  |
| global.enav_service.cloud_config.branch | string | `"master"` |  |
| global.enav_service.cloud_config.password | string | `"enav_config_password"` |  |
| global.enav_service.cloud_config.uri | string | `"http://enav-eureka.enav.svc.k8s:8761/config/"` |  |
| global.enav_service.cloud_config.username | string | `"enav_config_user"` |  |
| global.eureka.config_repo.branch | string | `"master"` |  |
| global.eureka.config_repo.password | string | `"git_password"` |  |
| global.eureka.config_repo.uri | string | `"https://git.com/gla-rad/eNav-Config.git"` |  |
| global.eureka.config_repo.username | string | `"git_user"` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"ghcr.io/gla-rad/enav-eureka"` |  |
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
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| readinessProbe.httpGet.path | string | `"/actuator/health/readiness"` |  |
| readinessProbe.httpGet.port | string | `"http"` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `8761` |  |
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
| volumes[2].projected.sources[0].secret.name | string | `"eureka-secrets"` |  |
| volumes[2].projected.sources[1].secret.items[0].key | string | `"truststore"` |  |
| volumes[2].projected.sources[1].secret.items[0].path | string | `"truststore.jks"` |  |
| volumes[2].projected.sources[1].secret.name | string | `"eureka-secrets"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.13.1](https://github.com/norwoodj/helm-docs/releases/v1.13.1)