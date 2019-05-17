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

## Cluster & Nodes

Print cluster name

```bash
kubectl config current-context
```

Get cluster nodes

```bash
kubectl get nodes
```

## Pods, Services, Deployments

Apply resource definitions

```bash
kubectl create|apply -f <file.yaml>
```

List resources

```bash
kubectl get pods|rcs|services|deployments
```

Delete pods

```bash
kubectl delete pods <pod_name>
```

Get specific service and follow changes 

```bash
kubectl get service <Service_name> --watch
```

Print pod logs

```bash
kubectl logs <pod_name>
```

Print all events

```bash
kubectl get events --sort-by=.metadata.creationTimestamp
```

## Namespaces

List namespace

```bash
kubectl get namespace
```

You can permanently save the namespace for all subsequent kubectl commands in that context.

```bash
kubectl config set-context $(kubectl config current-context) --namespace=<insert-namespace-name-here>
# Validate it
kubectl config view | grep namespace:
```