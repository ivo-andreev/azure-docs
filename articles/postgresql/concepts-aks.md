---
title: Connect to Azure Kubernetes Service - Azure Database for PostgreSQL - Single Server
description: Learn about connecting Azure Kubernetes Service (AKS) with Azure Database for PostgreSQL - Single Server
ms.service: postgresql
ms.subservice: single-server
ms.topic: conceptual
ms.author: sunila
author: sunilagarwal
ms.reviewer: ""
ms.date: 07/14/2020
---

# Connecting Azure Kubernetes Service and Azure Database for PostgreSQL - Single Server

Azure Kubernetes Service (AKS) provides a managed Kubernetes cluster you can use in Azure. Below are some options to consider when using AKS and Azure Database for PostgreSQL together to create an application.

## Accelerated networking
Use accelerated networking-enabled underlying VMs in your AKS cluster. When accelerated networking is enabled on a VM, there is lower latency, reduced jitter, and decreased CPU utilization on the VM. Learn more about how accelerated networking works, the supported OS versions, and supported VM instances for [Linux](../virtual-network/create-vm-accelerated-networking-cli.md).

From November 2018, AKS supports accelerated networking on those supported VM instances. Accelerated networking is enabled by default on new AKS clusters that use those VMs.

You can confirm whether your AKS cluster has accelerated networking:
1. Go to the Azure portal and select your AKS cluster.
2. Select the Properties tab.
3. Copy the name of the **Infrastructure Resource Group**.
4. Use the portal search bar to locate and open the infrastructure resource group.
5. Select a VM in that resource group.
6. Go to the VM's **Networking** tab.
7. Confirm whether **Accelerated networking** is 'Enabled.'

Or through the Azure CLI using the following two commands:
```azurecli
az aks show --resource-group myResourceGroup --name myAKSCluster --query "nodeResourceGroup"
```
The output will be the generated resource group that AKS creates containing the network interface. Take the "nodeResourceGroup" name and use it in the next command. **EnableAcceleratedNetworking** will either be true or false:
```azurecli
az network nic list --resource-group nodeResourceGroup -o table
```

## Connection pooling
A connection pooler minimizes the cost and time associated with creating and closing new connections to the database. The pool is a collection of connections that can be reused. 

There are multiple connection poolers you can use with PostgreSQL. One of these is [PgBouncer](https://pgbouncer.github.io/). In the Microsoft Container Registry, we provide a lightweight containerized PgBouncer that can be used in a sidecar to pool connections from AKS to Azure Database for PostgreSQL. Visit the [docker hub page](https://hub.docker.com/r/microsoft/azureossdb-tools-pgbouncer/) to learn how to access and use this image. 

## Next steps

Create an AKS cluster [using the Azure CLI][./learn/quick-kubernetes-deploy-cli], [using Azure PowerShell][./learn/quick-kubernetes-deploy-powershell], or [using the Azure portal][./learn/quick-kubernetes-deploy-portal].
