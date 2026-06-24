# Flux System — Currently Disabled

Flux Kustomization and GitRepository were removed after a k3s hairpin NAT issue
prevented the source-controller from cloning from Forgejo via SSH within the cluster.

## Re-enable when ready:
1. Ensure Forgejo is stable at https://git.spark.homelab.lan
2. Apply: kubectl apply -f flux-system/gitrepository.yaml
3. Apply: kubectl apply -f flux-system/kustomization.yaml
4. Verify: flux get kustomization -A

## Known issues:
- Pod → NodePort → same host (hairpin NAT) breaks SSH cloning from within k3s
- Fix options: HTTP+Token auth, or switch to git-daemon for local repos
