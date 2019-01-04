# Commands

Acount login
```
az login
```

## Azure Container Registry

get login server name
```
az acr list --resource-group <resource_group> --query "[].{acrLoginServer:loginServer}" --output table
```

login
```
az acr login --name <acr_name>
```

list images
```
az acr repository list --name <acr_name>  --output table
```

list all tags
```
az acr repository show-tags --name <acr_name> --repository <repository_for_specofoc_image> -o table
```

show password of registry
```
az acr credential show --name <acr_name> --query "passwords[0].value"
```

## Azure Container Instances

list containers
```
az container list --resource-group <resource_group> -o table
```

create containers
```
az container create \
--resource-group adp-cassandra \
--name <container_name> \
--image <docker_image> \
--cpu 4 \
--memory 8 \
--registry-username <acr_name> \
--registry-password <password> \
--dns-name-label <name_for_dns> \
--ports 80
```

delete container
```
az container delete --name  <container_name> --resource-group <resource_group> -o table --yes -y
```
