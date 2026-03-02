# kafka-broker

A Helm chart for the Kafka Broker of the GLA e-Navigation Service Architecture

![Version: 0.0.3](https://img.shields.io/badge/Version-0.0.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 3.9.0](https://img.shields.io/badge/AppVersion-3.9.0-informational?style=flat-square)

## The e-Navigation Kafka Broker Service

IALA Guideline G1114 makes reference to a Maritime Messaging Service amongst its
value-added data processing services. In the current implementation, the
“Message Broker” assumes this role and facilitates a geospatially-aware
publish-subscribe communication pattern (through the use of the
[GeoMesa](https://www.geomesa.org) library), where the senders of messages
(publishers) do not program the messages to be send directly to a specific
receiver (consumers). Instead, publishers submit the messages to a specific
topic, so that all authorised services interested in that topic and the affected
geographical location will receive them. The underlying publish-subscribe
functionality is achieved via an [Apache Kafka](https://kafka.apache.org/)
broker, provided by this chart.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| env[0].name | string | `"KAFKA_BROKER_ID"` |  |
| env[0].valueFrom.configMapKeyRef.key | string | `"broker_id"` |  |
| env[0].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[10].name | string | `"CLUSTER_ID"` |  |
| env[10].valueFrom.configMapKeyRef.key | string | `"cluster_id"` |  |
| env[10].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[11].name | string | `"KAFKA_MESSAGE_MAX_BYTES"` |  |
| env[11].valueFrom.configMapKeyRef.key | string | `"message_max_bytes"` |  |
| env[11].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[12].name | string | `"KAFKA_MAX_REQUEST_SIZE"` |  |
| env[12].valueFrom.configMapKeyRef.key | string | `"max_request_size"` |  |
| env[12].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[1].name | string | `"KAFKA_LISTENER_SECURITY_PROTOCOL_MAP"` |  |
| env[1].valueFrom.configMapKeyRef.key | string | `"listener_security_protocol_map"` |  |
| env[1].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[2].name | string | `"KAFKA_ADVERTISED_LISTENERS"` |  |
| env[2].valueFrom.configMapKeyRef.key | string | `"advertised_listeners"` |  |
| env[2].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[3].name | string | `"KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR"` |  |
| env[3].valueFrom.configMapKeyRef.key | string | `"offsets_topic_replication_factor"` |  |
| env[3].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[4].name | string | `"KAFKA_PROCESS_ROLES"` |  |
| env[4].valueFrom.configMapKeyRef.key | string | `"process_roles"` |  |
| env[4].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[5].name | string | `"KAFKA_NODE_ID"` |  |
| env[5].valueFrom.configMapKeyRef.key | string | `"node_id"` |  |
| env[5].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[6].name | string | `"KAFKA_CONTROLLER_QUORUM_VOTERS"` |  |
| env[6].valueFrom.configMapKeyRef.key | string | `"controller_quorum_voters"` |  |
| env[6].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[7].name | string | `"KAFKA_LISTENERS"` |  |
| env[7].valueFrom.configMapKeyRef.key | string | `"kafka_listeners"` |  |
| env[7].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[8].name | string | `"KAFKA_INTER_BROKER_LISTENER_NAME"` |  |
| env[8].valueFrom.configMapKeyRef.key | string | `"inter_broker_listener_name"` |  |
| env[8].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| env[9].name | string | `"KAFKA_CONTROLLER_LISTENER_NAMES"` |  |
| env[9].valueFrom.configMapKeyRef.key | string | `"controller_listener_name"` |  |
| env[9].valueFrom.configMapKeyRef.name | string | `"kafka-broker-config"` |  |
| fullnameOverride | string | `""` |  |
| global.kafka_broker.advertised_listeners | string | `"PLAINTEXT://kafka-broker.enav:9092,PLAINTEXT_HOST://localhost:19092"` |  |
| global.kafka_broker.broker_id | string | `"1"` |  |
| global.kafka_broker.cluster_id | string | `"R3JhZElzVGhlQmVzdA"` |  |
| global.kafka_broker.controller_listener_name | string | `"CONTROLLER"` |  |
| global.kafka_broker.controller_quorum_voters | string | `"1@localhost:29093"` |  |
| global.kafka_broker.inter_broker_listener_name | string | `"PLAINTEXT"` |  |
| global.kafka_broker.kafka_listeners | string | `"PLAINTEXT://kafka-broker.enav:9092,CONTROLLER://localhost:29093,PLAINTEXT_HOST://0.0.0.0:19092"` |  |
| global.kafka_broker.listener_security_protocol_map | string | `"PLAINTEXT:PLAINTEXT,PLAINTEXT_HOST:PLAINTEXT,CONTROLLER:PLAINTEXT"` |  |
| global.kafka_broker.max_request_size | string | `"10485760"` |  |
| global.kafka_broker.message_max_bytes | string | `"10485760"` |  |
| global.kafka_broker.node_id | string | `"1"` |  |
| global.kafka_broker.offsets_topic_replication_factor | string | `"1"` |  |
| global.kafka_broker.process_roles | string | `"broker,controller"` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"apache/kafka"` |  |
| image.tag | string | `""` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `""` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls | list | `[]` |  |
| kraft.enabled | bool | `true` |  |
| nameOverride | string | `""` |  |
| nodeSelector."kubernetes.io/os" | string | `"linux"` |  |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `9092` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.automount | bool | `true` |  |
| serviceAccount.create | bool | `false` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` |  |
| volumeMounts | list | `[]` |  |
| volumes | list | `[]` |  |
| zookeeper.enabled | bool | `false` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.13.1](https://github.com/norwoodj/helm-docs/releases/v1.13.1)