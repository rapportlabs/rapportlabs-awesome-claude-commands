# Rapport Labs Awesome Claude Commands

This repository contains custom Claude commands and DevOps automation scripts for Rapport Labs infrastructure management.

## Prerequisites

Before running any DevOps commands, ensure that helm-mcp is configured in your MCP settings with the following configuration:

```json
"helm": {
  "type": "stdio",
  "command": "docker",
  "args": [
    "run",
    "-i",
    "-e",
    "CHARTMUSEUM_URL=https://chartmuseum.rapportlabs.cloud",
    "-e",
    "CHARTMUSEUM_USERNAME=***",
    "-e",
    "CHARTMUSEUM_PASSWORD=***",
    "279182450151.dkr.ecr.ap-northeast-2.amazonaws.com/mcp/helm:0.4.3",
    "python",
    "app.py",
    "--transport",
    "stdio"
  ]
}
```

This configuration is required for accessing the Chartmuseum repository to retrieve helm chart versions and configurations.

## DevOps Commands

### ArgoCD Application Initialization

The main automation workflow in this repository is ArgoCD application initialization. See `devops/argocd-app-init.md` for detailed specifications.

## Related Repositories

This repository works in conjunction with:
- `rapportlabs-argocd` - ArgoCD configurations and manifests
- `rapportlabs-kubernetes` - Kubernetes charts and configurations