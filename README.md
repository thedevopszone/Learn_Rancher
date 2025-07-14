# Learn Rancher


- 3 Nodes
- selinux
- hostnames



```
sudo cat /var/lib/rancher/rke2/server/node-token
K10545039017ecb1fa142e822e56e77c25b57970431de64c5c888104b2780109acc::server:f966d0489b1cf5b776e9ac08ace4c626
```


First Node
```
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="server" K3S_TOKEN=some-auth-token K3S_CLUSTER_INIT=1 sh -

export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
alias k=kubectl

sudo cat /var/lib/rancher/k3s/server/node-token

systemctl disable firewalld --now
```

If you wish to keep firewalld enabled, by default, the following rules are required:
```
firewall-cmd --permanent --add-port=6443/tcp #apiserver
firewall-cmd --permanent --zone=trusted --add-source=10.42.0.0/16 #pods
firewall-cmd --permanent --zone=trusted --add-source=10.43.0.0/16 #services
firewall-cmd --reload
```



Node2 and Node3
```
curl -sfL https://get.k3s.io | \
K3S_URL=https://172.16.0.30:6443 \
K3S_TOKEN="K10ba6c5f1e88cc84cae6efd24b091240cb7bd935000cc836367e777c24627fadaa::server:3dfd20ec80cbcd2b01cc31eb9833d278" \
INSTALL_K3S_EXEC="--with-node-id" \
sh -

#curl -sfL https://get.k3s.io | K3S_URL=https://35.158.118.7:6443 INSTALL_K3S_EXEC="server" K3S_TOKEN="some-auth-token" sh -
```

```
sudo dnf install tar
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









