Kubectl Commands
--------------------------------
minikube start --cpus 2 --memory 4096
minikube.exe start --cpus 2 --memory 8196 --insecure-registry "35.156.234.183"
minikube.exe start --kubernetes-version="v1.11.0" --vm-driver="virtualbox" --alsologtostderr
minikube.exe start --kubernetes-version="v1.11.0" --vm-driver="virtualbox" --alsologtostderr --insecure-registry "35.156.234.183"
minikube start --docker-env HTTP_PROXY=http://198.138.0.6:9400 --docker-env HTTPS_PROXY=https://198.138.0.6:9400 --docker-env NO_PROXY=localhost,127.0.0.0/8,192.0.0.0/8 --kubernetes-version="v1.11.0" --vm-driver="virtualbox" --alsologtostderr
minikube start --docker-env="http_proxy=http://198.138.0.6:9400" --docker-env="https_proxy=https://198.138.0.6:9400"

minikube dashboard
minikube service outage-management-service --url

kubectl run outage-management --image=35.156.234.183:5000/noms/outage-management:0.0.1
kubectl run topo-tracer --image=35.156.234.183:5000/noms/topo-tracer:0.0.1

======================================================================

kubectl config current-context

kubectl create|apply -f <file.yml>
kubectl delete pods <pod_name>

kubectl get nodes
kubectl get pods|rcs|services|deployments

kubectl logs <pod_name>
kubectl get events --sort-by=.metadata.creationTimestamp





======================================================================






