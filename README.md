# Hands on with Kubernetes Workshop Series - Azure Container Service

The following repository will help you create a Kubernetes cluster running on Azure Container Service:

1. Sign up for an Azure account:
    1. FREE TRIAL: $200 of Azure Credits https://azure.microsoft.com/en-us/free/

## Course Documents

Join the course's Slack:

 [![Kismatic Slack Signup](http://54.242.94.98/badge.svg)](http://54.242.94.98/)

You will find the presentation, links, commands and group questions pinned in the _#k8straining_ channel

## Using Kubernetes

The presenter will go through a list of demos during the workshop.

Find the demos [here](docs/demos)

## Fill Out Survey! 

We really enjoy your feedback! 

Find the survey [here](https://goo.gl/forms/xleficwP525Y7nXY2)

## Create Infrastructure & Provision Cluster

A list of steps to build and provision the Kubernetes cluster can be found [here](docs/3-build-cluster.md)

## Destroying Cluster After Training

Congrats on finishing the hands on introduction to Kubernetes!

To remove the Kubernetes cluster and underlying infrastructure execute the following from the Azure Cloud Shell

```
az group delete --name myResourceGroup --yes --no-wait
```

## Reference

Kubernetes vs. Mesos Marathon vs. Docker Swarm vs. Cloud Foundry SWOT analysis found [here](https://apprenda.com/white-papers/container-orchestration-comparison-guide/)

Google Cloud Podcast with John Wilkes, one of the engineers from Google who originally developed their internal container orchestration system - Borg [here](https://www.gcppodcast.com/post/episode-46-borg-and-k8s-with-john-wilkes/)

Learn Why CTO's and Developers are Choosing Kubernetes [here](https://apprenda.com/why-kubernetes/)

Join the Kubernetes community [here](https://github.com/apprenda/hands-on-with-kubernetes-gke/blob/master/community.md)

***Kubernetes command line (Kubectl) cheat sheet*** [here](https://kubernetes.io/docs/user-guide/kubectl-cheatsheet/)


## Brought To You By

![Apprenda](https://upload.wikimedia.org/wikipedia/commons/c/cc/Apprenda_logo.png)


