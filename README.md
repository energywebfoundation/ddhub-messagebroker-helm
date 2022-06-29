# ddhub-messagebroker

![Version: 1.2.0](https://img.shields.io/badge/Version-1.2.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.3.0](https://img.shields.io/badge/AppVersion-0.3.0-informational?style=flat-square)

A Helm chart for Kubernetes
## Introduction
This is a repository with helm chart for DDhub-messagebroker. For more information about DDhub messagebroker please check the [repository](https://github.com/energywebfoundation/ddhub-message-broker).
## Quickstart
``` minikube start
create a secret with required environment variables (blueprint below) NOTE: all the secret data will be loaded as environment variables.
apiVersion: v1 kind: Secret metadata: name: ddhub-messagebroker-test-secret type: Opaque data: MONGODB_CONNECTION_STRING: base64(PRIVATE_KEY) MONGODB_DB_NAME: base64(JWT_SECRET) ...
kubectl apply -f secret.yaml
helm install ddhub-messagebroker-test https://github.com/energywebfoundation/ddhub-messagebroker-helm/archive/refs/tags/v1.1.4.zip
kubectl get pods ```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| fullnameOverride | string | `"ddhub-messagebroker-test"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"aemoprivatecontainerregistry.azurecr.io/ddhub-messagebroker"` |  |
| image.tag | string | `"canary"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations."kubernetes.io/ingress.class" | string | `"azure/application-gateway"` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"ddhub-test.energyweb.org"` |  |
| ingress.hosts[0].paths[0].backend.service.name | string | `"ddhub-messagebroker-test"` |  |
| ingress.hosts[0].paths[0].backend.service.port.number | int | `80` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls | list | `[]` |  |
| messagebroker.config.blob_storage_container | string | `"file"` | (optional string, default file) the container name for uploaded files in blob storage |
| messagebroker.config.cacheServerUrl | string | `"https://identitycache-staging.energyweb.org/v1"` | (optional string, default https://identitycache-dev.energyweb.org/) An URL to Identity Cache server, more info https://github.com/energywebfoundation/iam-cache-server |
| messagebroker.config.context_url | string | `"https://ddhub-test.energyweb.org"` | (optional string, default https://ddhub-test.energyweb.org) the ddhub server url |
| messagebroker.config.http_body_size_max | string | `"122880k"` | (optional string, default 122880k) the http request body max limit |
| messagebroker.config.jwt_issuer | string | `"https://ddhub-test.energyweb.org"` | (optional string, default https://ddhub-test.energyweb.org matching ingress) jwt token issuer |
| messagebroker.config.mbDid | string | `"did:ethr:0x5aEa5Bf5c5b341A0BF30Cc5b51b77Fb9807F1b52"` | (required string) it is the DID identifier corresponding to the PRIVATE_KEY |
| messagebroker.config.mongodb_pool_size_max | int | `10` | (optional string, default file) the container name for uploaded files in blob storage |
| messagebroker.config.mongodb_pool_size_min | int | `5` | (optional string, default file) the container name for uploaded files in blob storage |
| messagebroker.config.natsClusterUrl | string | `"nats://dsb-nats.nats.svc:4222"` | NATS Jetstream node url |
| messagebroker.config.port | int | `9000` | (optional int, default 3000) Port number to be used by DSB Message Broker to listen to |
| messagebroker.config.swagger_theme | string | `"original"` | (optional string, default original) the swagger UI theme |
| messagebroker.config.swagger_title | string | `"DDHub Message Broker"` | (optional string, default file) the swagger UI page title |
| messagebroker.config.webUrl | string | `"https://volta-rpc.energyweb.org/"` | (optional string, default https://volta-rpc.energyweb.org/) An URL to EW blockchain node (default |
| messagebroker.config.withSwagger | string | `"true"` | (optional bool, default true) Boolean that enables or disables hosting Swagger API documentation alongside DSB Message Broker endpoints, if true then http://{URL}:{PORT}/swagger is available |
| nameOverride | string | `"ddhub-messagebroker-test"` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `80` |  |
| service.type | string | `"LoadBalancer"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
