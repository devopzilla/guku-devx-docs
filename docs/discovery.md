---
sidebar_position: 5
---

# 🔭 Capability discovery

Discover platform capabilities
```bash
➜ devx project discover    
[🏷️  traits] "guku.io/devx/v1/traits"
traits.#Workload        a component that runs containers 
traits.#Replicable      a component that can be horizontally scaled 
traits.#Exposable       a component that has endpoints that can be exposed 
traits.#Volume  a component that has a volume 
traits.#Postgres        a postgres database 
traits.#Helm    a helm chart using helm repo 
traits.#HelmGit a helm chart using git 
traits.#HelmOCI a helm chart using oci 
traits.#Workflow        an automation workflow 
```

Discover transformers
```bash
➜ devx project discover -t
[🏷️  traits] "guku.io/devx/v1/traits"
traits.#Workload        a component that runs containers 
traits.#Replicable      a component that can be horizontally scaled 
traits.#Exposable       a component that has endpoints that can be exposed 
traits.#Volume  a component that has a volume 
traits.#Postgres        a postgres database 
traits.#Helm    a helm chart using helm repo 
traits.#HelmGit a helm chart using git 
traits.#HelmOCI a helm chart using oci 
traits.#Workflow        an automation workflow 

[🏭 transformers] "guku.io/devx/v1/transformers/argocd"
argocd.#AddHelmRelease  add a helm release 

[🏭 transformers] "guku.io/devx/v1/transformers/compose"
compose.#AddComposeService      add a compose service 
compose.#AddComposeVolume       add a compose service 
compose.#ExposeComposeService   expose a compose service ports 
compose.#AddComposePostgres     add a compose service for a postgres database 
compose.#AddComposeBuild        add compose build filed to build an image locally 

[🏭 transformers] "guku.io/devx/v1/transformers/gitlab"
gitlab.#AddCIPipeline

[🏭 transformers] "guku.io/devx/v1/transformers/istio"
istio.#AddAuthorizationPolicy

[🏭 transformers] "guku.io/devx/v1/transformers/kubernetes"
kubernetes.#AddDeployment
kubernetes.#AddService
kubernetes.#AddReplicas
kubernetes.#AddPodLabels
kubernetes.#AddPodAnnotations
kubernetes.#AddNamespace
kubernetes.#AddLabels
kubernetes.#AddPodTolerations
kubernetes.#AddPodSecurityContext
kubernetes.#AddWorkloadVolumes
kubernetes.#AddWorkloadProbes

[🏭 transformers] "guku.io/devx/v1/transformers/terraform"
terraform.#AddHelmRelease       add a helm release 
```