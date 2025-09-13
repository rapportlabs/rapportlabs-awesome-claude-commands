# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This repository contains custom Claude commands and DevOps automation scripts for Rapport Labs infrastructure management. The main focus is on ArgoCD application initialization and management workflows.

## Architecture

The repository is structured as a collection of DevOps utilities and automation commands:

- `devops/` - Contains DevOps automation documentation and workflows
  - `argocd-app-init.md` - Specification for ArgoCD application initialization command

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

## ArgoCD Application Initialization Workflow

The primary workflow in this repository is the ArgoCD application initialization process defined in `devops/argocd-app-init.md`. When implementing this workflow:

### Required User Inputs
- Service name
- Whether it's a microservice (boolean)
- Environment (dev, stg, prod, util)

### Microservice Template References
For microservices, reference these template structures:
- `rapportlabs-argocd/service-${env}-cluster/argocd-manifests/service-backend/templates/damoa-order.yaml`
- `rapportlabs-argocd/service-${env}-cluster/helm-charts/service-backend/damoa-order`

### Non-Microservice Template References
For non-microservices, reference these template structures:
- `rapportlabs-argocd/util-cluster/argocd-manifests/infra/templates/librechat.yaml`
- `rapportlabs-argocd/util-cluster/helm-charts/infra/librechat`

### Template Customization Rules
1. For microservices: Replace service-specific names (e.g., "order" → "referral")
2. Clear environment-specific variables in `serviceEnvs` and `bootstrap` sections, mark as `#TODO`
3. Use latest "microservice" helm chart version from Chartmuseum (check via MCP)
4. For non-microservices: Initialize `extra-manifests` directory with empty `dummy.yaml`
5. Mark uncertain configuration options as `#TODO`

## Related Repositories

This repository works in conjunction with:
- `~/work/rapportlabs-argocd` - ArgoCD configurations and manifests
- `~/work/rapportlabs-kubernetes` - Kubernetes charts and configurations

## Development Notes

- No build commands or test frameworks are present in this repository
- Content is primarily documentation-driven
- Focus on template generation and configuration management
- Ensure synchronization with related ArgoCD and Kubernetes repositories when making changes