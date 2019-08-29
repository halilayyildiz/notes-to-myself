# Kubectl Commands

## Context

Show config

```bash
kubectl config view
```

List k8s contexts

```bash
kubectl config get-contexts
```

Show current context

```bash
kubectl config current-context
```

Set current context

```bash
kubectl config current-context <context_name>
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

Get detailed info of node

```bash
kubectl describe  node <node_name>
```

## Pods, Services, Deployments

Apply object definitions

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

Get specific service and watch changes

```bash
kubectl get service <Service_name> --watch
```

Print pod logs

```bash
kubectl logs <pod_name>
```

Print pods with node information

```bash
kubectl get pods -o wide --sort-by="{.spec.nodeName}"
```

Print all events and watch

```bash
kubectl get events --sort-by=.metadata.creationTimestamp -w
```

Get a shell to the running container

```bash
kubectl exec -it <pod_name> -- /bin/bash
```

Scale pods

```bash
kubectl scale deployment <deployment_name> --replicas=0
```

List endpoints

```bash
kubectl get endpoints
```

List pods behind a endpoint

```bash
kubectl get endpoints <endpoint> -o=jsonpath='{.subsets[*].addresses[*].ip}' | tr ' ' '\n' | xargs -I % kubectl get pods --field-selector=status.podIP=%
```

## Namespaces

List namespaces

```bash
kubectl get namespace
```

Permanently save the namespace for all subsequent kubectl commands in that context.

```bash
kubectl config set-context $(kubectl config current-context) --namespace=<insert-namespace-name-here>
# Validate it
kubectl config view | grep namespace:
```

Not all objects are in a namespace

```bash
# In a namespace
kubectl api-resources --namespaced=true
# Not in a namespace
kubectl api-resources --namespaced=false
```

List specific apps under some specific namespace

```bash
kubectl get service -l app=<name> --namespace <namespace>
```

## Monitoring

Display resource usage of nodes|pods

```bash
kubectl top node|pod
```
