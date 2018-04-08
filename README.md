# Hands on with Kubernetes Workshop Series - Azure Container Service

The following repository will help you create a Kubernetes cluster running on Azure Container Service:

1. Sign up for an Azure account:
    1. FREE TRIAL: $200 of Azure Credits https://azure.microsoft.com/en-us/free/


## Using Kubernetes

The presenter will go through a list of demos during the workshop.

Find the demos [here](docs/demos)



## Create Infrastructure & Provision Cluster

A list of steps to build and provision the Kubernetes cluster can be found [here](docs/3-build-cluster.md)

## Destroying Cluster After Training

Congrats on finishing the hands on introduction to Kubernetes!

To remove the Kubernetes cluster and underlying infrastructure execute the following from the Azure Cloud Shell

```
az group delete --name myResourceGroup --yes --no-wait
```




