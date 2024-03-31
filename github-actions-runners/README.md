Before syncing the helmfile you need to create the PAT secret in two namespaces.

The PAT should have the 'repo' scope for repository runners and 'admin:org' for organization runners.

```shell
kubectl create namespace github-arc-systems && \
kubectl create namespace github-arc-runners

export PAT='VALUE' && \
kubectl create secret generic pat-secret --namespace=github-arc-systems --from-literal=github_token=$PAT && \
kubectl create secret generic pat-secret --namespace=github-arc-runners --from-literal=github_token=$PAT
```