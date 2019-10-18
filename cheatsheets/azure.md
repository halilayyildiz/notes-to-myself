# Azure CLI Commands

Interactive login

```bash
az login
```

List your accounts

```bash
az account list
```

Show active account

```bash
az account show
```

Change active account for CLI

```bash
az account set --subscription <subscription ID>
```

## Azure Container Registry

get login server name

```bash
az acr list --resource-group <resource_group> --query "[].{acrLoginServer:loginServer}" --output table
```

login to container registry

```bash
az acr login --name <acr_name>
```

list images under some repo

```bash
az acr repository list --name <acr_name>  --output table
```

list all tags under some repo

```bash
az acr repository show-tags --name <acr_name> --repository <repository> -o table
```

show password of the registry

```bash
az acr credential show --name <acr_name> --query "passwords[0].value"
```

## Azure Container Instances

list container instances

```bash
az container list --resource-group <resource_group> -o table
```

create container instance with identity assigment and environment variables

```bash
az container create \
--resource-group <resource_group> \
--name <container_name> \
--image <docker_image> \
--cpu 2 \
--memory 8 \
--registry-username <acr_name> \
--registry-password <password> \
--dns-name-label <name_for_dns> \
--ports 80
--assign-identity /subscriptions/<subscription_id>/resourceGroups/<resource_group>/providers/Microsoft.ManagedIdentity/userAssignedIdentities/<user_assigned_identity> \
--environment-variables \
    STORAGE_ACCOUNT=<storage_account> \
    AZURE_KEYVAULT_URL=https://somekeyvault.vault.azure.net/
```

delete container instance

```bash
az container delete --name  <container_name> --resource-group <resource_group> -o table --yes -y
```

## Azure Kubertenes (AKS)

create new k8s cluster

```bash
# create resource group
az group create --name h3l-k8s --location westeurope
# create kubernetes cluster
az aks create --resource-group h3l-k8s --name adp-h3l-k8s --node-count 2 --node-vm-size Standard_D1_v2 --generate-ssh-keys
```

configure kubectl to connect to your k8s cluster

```bash
# setup credentials
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
```

start the k8s dashboard

```bash
az aks browse --resource-group myResourceGroup --name myAKSCluster
```

```bash
az aks show --resource-group <resource_group> --name <myAKSCluster> --query <nodeResourceGroup> -o tsv
```


