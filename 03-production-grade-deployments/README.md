# Production-grade Deployments

* Deploy application

```sh
kubectl apply -f web-application/deployment/deployment.yaml -f web-application/deployment/service.yaml
```

* Check pods and figure out why pods are pending

```sh
kubectl get pods
kubectl describe pods
```

* Label Nodes

```sh
kubectl get nodes
kubectl label nodes --all storagetype=ssd
```

* See that pods are schedules

```sh
kubectl get pods
```

* Update deployment

```sh
kubectl apply -f web-application/deployment/deployment-2.yaml
```

* Add PodDisruptionBudget

```sh
kubectl apply -f web-application/deployment/pdb.yaml
```

* Create autoscaler

```sh
kubectl autoscale deployment web-application --min=2 --max=6 --cpu-percent=2
kubectl get horizontalpodautoscaler
kubectl describe horizontalpodautoscalers web-application
kubectl top pods
```

* Watch pods and create traffic

```sh
watch kubectl get pods
ab -c 100 -n 1000 http://<IP_ADDRESS>/
```

* Remove autoscaler

```sh
kubectl delete horizontalpodautoscalers.autoscaling web-application
```

* Scale deployment down again

```sh
kubectl scale deployment web-application --replicas 2
```
