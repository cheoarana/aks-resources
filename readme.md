# AKS Resources

## Overview

This repository is offered to support the start of the great world of kubernetes in Azure.



## Project structure

```
.
├── aks-resources
│   ├──deployment-service
│   │    └── aks.yml
│   ├──ingress
│   │    └── ingress-rules.yml
│   └──namespace
│        └── namespace.yaml
├── LICENSE
└── readme.md
```

## Secret TLS
As a prerequisite to run the manifest files, a tls secret must be created, for this purpose use the following command as follows 

```sh
kubectl create secret tls cheoarana-tls --namespace ns-cheoarana --key key_file.key --cert cert_file.crt  
```



## Ingress
For ingress, the variables are explained as follows
| Variable | Example                                        |
| -------- | ---------------------------------------------- |
| `[domain].[com]` | `"myamazingdomain.com"`                |
| `[subdomain].[domain].[com]` | `test.myamazingdomain.com` |
| `[port]` | `8080`                                         |

## Manifest files
`aks.yml` file contains the configuration of a deployment and a service for better automation. 

## Execution/use of manifest files

#### namespace
Variables contained in the `namespace.yaml` file 
| Variable | Example                                        |
| -------- | ---------------------------------------------- |
| **NAMESPACE_NAME** | Variable to replace with the namespace name |

**LINUX:**
```sh
NAMESPACE_NAME=ns-cheoarana  envsubst <namespace/namespace.yaml> namespace-cheoarana.yaml
```

#### deployment-service
Variables contained in the `aks.yml` file 
| Variable | Example                                        |
| -------- | ---------------------------------------------- |
| **AKS_IMAGE_NAME** | Variable to replace with the docker image name  |
| **NAMESPACE_NAME** | Variable to replace with the namespace name |
| **CONTAINER_REGISTRY_NAME** | Variable to be replaced by the name of the registry container |
| **BUILD_BUILDID** | Variable to replace by docke image version number |
| **ENVIRONMENT** | Variable to replace with the name of the environment |

**LINUX:**
```sh
AKS_IMAGE_NAME=cheoarana/rest-hello-world NAMESPACE_NAME=ns-cheoarana CONTAINER_REGISTRY_NAME=acrcheoarana BUILD_BUILDID=1.0 ENVIRONMENT=production envsubst <deployment-service/aks.yml> aks-cheoarana.yml
```


#### ingress
Variables contained in the `ingress-rules.yml` file 
| Variable | Example                                        |
| -------- | ---------------------------------------------- |
| **INGRESS_NAME** | Variable to replace with the ingress name  |
| **NAMESPACE_NAME** | Variable to replace with the namespace name |
| **TLS_SECRET_NAME** | Variable to replace with the ssl secret name |
| **PATH_PREFIX** | Variable to be replaced by the path of endpoint |
| **NAME_SERVICE** | Variable to be replaced by the name of the service deployed in the previous step |
| **PATH_PREFIX_2** | Variable to be replaced by the path of second endpoint|
| **NAME_SERVICE_2** | Variable to be replaced by the name of the service deployed in the previous step |

**LINUX:**
```sh
INGRESS_NAME=cheoarana-ingress NAMESPACE_NAME=ns-cheoarana TLS_SECRET_NAME=cheoarana-tls PATH_PREFIX=/ NAME_SERVICE=cheoarana/rest-hello-world PATH_PREFIX_2=/api/v1 NAME_SERVICE_2=cheoarana/backend envsubst <ingress/ingress-rules.yml> ingress-rules-cheoarana.yaml
```
## License

This library is licensed under the MIT-0 License. See the [LICENSE](./LICENSE) file.

## Links

- [Ingress controller on Azure Kubernetes Service](https://learn.microsoft.com/en-us/azure/aks/ingress-tls?tabs=azure-cli)
