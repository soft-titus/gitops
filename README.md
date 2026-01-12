# GitOps

This repository contains the declarative configuration for managing multiple
Kubernetes clusters using the GitOps approach with Flux.

All cluster states, workloads, infrastructure components, and policies are
defined as version-controlled manifests stored in this repository. Flux
continuously reconciles these configurations against each cluster, ensuring they
remain consistent, reproducible, and drift-free.

## Cluster Bootstrap

```bash
flux bootstrap git \
  --components-extra=image-reflector-controller,image-automation-controller \
  --url=ssh://git@github.com/soft-titus/gitops.git \
  --branch=main \
  --path=env/<cluster-name> \
  --private-key-file=$HOME/.ssh/<private-key> \
  --password <ssh-key-passphrase>
```
