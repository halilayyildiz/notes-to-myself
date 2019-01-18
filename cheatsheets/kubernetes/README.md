# Kubectl Commands

```bash
minikube start --cpus 2 --memory 4096
```

```bash
minikube.exe start --cpus 2 --memory 8196 --insecure-registry "35.156.234.183"
```

```bash
minikube.exe start --kubernetes-version="v1.11.0" --vm-driver="virtualbox" --alsologtostderr
```

```bash
minikube.exe start --kubernetes-version="v1.11.0" --vm-driver="virtualbox" --alsologtostderr --insecure-registry "35.156.234.183"
```

open kubernetes dahsboard

```bash
minikube dashboard
```

```bash
minikube service <your_service> --url
```

```bash
kubectl run <service_name> --image=35.156.234.183:5000/noms/outage-management:0.0.1
```

## ------------

```bash
kubectl config current-context
```

```bash
kubectl create|apply -f <file.yml>
```

```bash
kubectl delete pods <pod_name>
```

```bash
kubectl get nodes
```

```bash
kubectl get pods|rcs|services|deployments
```

```bash
kubectl logs <pod_name>
```

```bash
kubectl get events --sort-by=.metadata.creationTimestamp
```
