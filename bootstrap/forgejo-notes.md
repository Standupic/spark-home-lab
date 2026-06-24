# Forgejo Bootstrap Strategy

Forgejo is deployed as a standard Kubernetes Deployment in platform/forgejo.yaml.
It is not a HelmRelease because:

1. The Flux git repo must exist BEFORE Flux can manage it
2. Managing Forgejo via Flux creates a chicken-and-egg problem
3. Forgejo's Helm chart requires additional tooling (Helm CLI or Flux HelmRelease)

Migration path when Forgejo is stable:
1. Push all manifests to Forgejo
2. Update flux-system/gitrepository.yaml URL to point at Forgejo
3. Flux continues reconciliation from Forgejo
4. Forgejo can optionally be added to Flux management post-migration
