# Rapport Labs Awesome Claude Commands

This repository is for sharing awesome custom slash commands for Claude Code. It contains custom Claude commands and DevOps automation scripts for Rapport Labs infrastructure management.

## New to Custom Slash Commands?

If you're not familiar with custom slash commands in Claude Code, please first read the documentation: https://docs.anthropic.com/en/docs/claude-code/slash-commands
You can use commands like this. 

<img width="1892" height="770" alt="87957" src="https://github.com/user-attachments/assets/05a4a7c9-c0b4-417d-b15b-9d02c4119daa" />


## How to Use This Repository

1. First, clone this repo
2. Then, symlink this repo as rpls/ in ~/.claude/commands
   ```bash
   ln -s ~/work/rapportlabs-awesome-claude-commands rpls
   ```

## Prerequisites

Before running any DevOps commands, ensure that helm-mcp is configured in your MCP settings for Claude Code (ex. `~/.claude.json`) with the following configuration:

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
