# Initialize ArgoCD Application Command


## Behavior

First ask the user for the inputs below.
- The service name
- Whether it's a microservice
- The environment (dev, stg, prod, util)

** If it's a microservice, you should refer to the directories below.
- rapportlabs-argocd/service-${env}-cluster/argocd-manifests/service-backend/templates/damoa-order.yaml
- rapportlabs-argocd/service-${env}-cluster/helm-charts/service-backend/damoa-order
For the values, you should wipe all the specific environment variables in serviceEnvs and bootstrap section, and leave them as #TODO.
Leave all the other options, but change the service name related settings. (ex. If the new service name is "referral", you should change "order" to "referral")
Always use the latest version of the "microservice" helm chart in Chartmueum, and check if the options are correct. You can find the latest chart version and the contents from MCP.

** If it's not a microservice, you should refer to the directory and files below.
- rapportlabs-argocd/util-cluster/argocd-manifests/infra/templates/librechat.yaml
- rapportlabs-argocd/util-cluster/helm-charts/infra/librechat
Initialize the extra-manifests directory with dummy.yaml, without any content.
If you are not certain about the options, leave as #TODO. 
