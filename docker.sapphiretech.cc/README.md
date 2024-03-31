Before syncing the helmfile you need to create the htpasswd secret in the namespace.

Generate htpasswd:
```shell
docker run --entrypoint htpasswd httpd:2 -Bbn user password >> ./htpasswd
```

```shell
kubectl create namespace docker-registry
kubectl create secret generic htpasswd --namespace=docker-registry --from-file=htpasswd=./htpasswd
```