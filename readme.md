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

## License

This library is licensed under the MIT-0 License. See the [LICENSE](./LICENSE) file.
