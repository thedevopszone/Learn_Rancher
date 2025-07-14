# Learn Rancher

First Node
```
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="server" K3S_TOKEN=some-auth-token K3S_CLUSTER_INIT=1 sh -

export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```

Node2 and Node3
```
curl -sfL https://get.k3s.io | K3S_URL=https://35.158.118.7:6443 INSTALL_K3S_EXEC="server" K3S_TOKEN="some-auth-token" sh -
```

```
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

```
helm repo add jetstack https://charts.jetstack.io
```

```
helm upgrade --install cert-manager jetstack/cert-manager --namespace cert-manager --set installCRDs=true --version v1.7.1 --create-namespace
```


```
helm repo add rancher-latest https://releases.rancher.com/server-charts/latest
```

```
helm upgrade --install rancher rancher-latest/rancher --namespace cattle-system --version v2.6.4 --set hostname=rancher.softxpert.duckdns.org --create-namespace --set ingress.tls.source=letsEncrypt
```

```
helm upgrade --install rancher rancher-latest/rancher --namespace cattle-system --version v2.6.4 --set hostname=softxpert.duckdns.org --create-namespace --set ingress.tls.source=letsEncrypt
```

```
k get ingress -m cattle-system
```









