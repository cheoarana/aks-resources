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

```sh
NAMESPACE_NAME=ns-cheoarana  envsubst <namespace/namespace.yaml> namespace-cheoarana.yaml
```

#### deployment-service
Variables contained in the `aks.yaml` file 
| Variable | Example                                        |
| -------- | ---------------------------------------------- |
| **AKS_IMAGE_NAME** | Variable to replace with the docker image name  |
| **NAMESPACE_NAME** | Variable to replace with the namespace name |
| **CONTAINER_REGISTRY_NAME** | Variable to be replaced by the name of the registry container |
| **BUILD_BUILDID** | Variable to replace by docke image version number |
| **ENVIRONMENT** | Variable to replace with the name of the environment |

```sh
AKS_IMAGE_NAME=cheoarana/rest-hello-world NAMESPACE_NAME=ns-cheoarana CONTAINER_REGISTRY_NAME=acrcheoarana BUILD_BUILDID=1.0 ENVIRONMENT=production envsubst <deployment-service/aks.yaml> aks-cheoarana.yaml
```
## License

This library is licensed under the MIT-0 License. See the [LICENSE](./LICENSE) file.
