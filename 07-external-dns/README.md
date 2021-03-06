# External DNS

* Install Helm: https://docs.helm.sh/using_helm/#installing-helm

```sh
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
```

* Replace all occurrences of `CHANGEME` in values.yaml with the provided secrets

* Install external-dns with Helm:

```sh
kubectl create namespace external-dns
```

```sh
helm upgrade --install external-dns --namespace=external-dns -f values.yaml bitnami/external-dns
```

* Replace occurrence of `YOUR_NAME` in nginx-test.yaml

* Deploy nginx test with dns entry:

```sh
kubectl apply -f nginx-test.yaml --namespace web-application
```
