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
### Linux
#### namespace
Variables contained in the `namespace.yaml` file 
| Variable | Example                                        |
| -------- | ---------------------------------------------- |
| **NAMESPACE_NAME** | Variable to replace with the namespace name |

```sh
NAMESPACE=ns-cheoarana  envsubst <namespace/namespace.yaml> namespace-cheoarana.yaml
```

## License

This library is licensed under the MIT-0 License. See the [LICENSE](./LICENSE) file.
