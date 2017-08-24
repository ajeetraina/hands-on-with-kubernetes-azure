# Build the Kubernetes Cluster

In this section, you will find code blocks with commands  for you to copy & paste into the Azure Cloud Shell (remote terminal window). We have excluded the command prompt itself (the dollar sign `$`) from the snippets. 

**Tips for those who have not used a command line in ages**

It may take few minutes for a command prompt to respond. However, if it ever gets stuck you can use `Ctrl+C` to interrupt the current command and get back to the command prompt. 

You can use the `Up Arrow` to navigate to previous commands in the command history. 

To copy from the terminal window, simply highlight the desired text and it will be auto-copied. You can then use paste it as usual.

## 1. Sign In To Azure

Navigate to the Azure Cloud portal: https://portal.azure.com

For this workshop we will use the web-based terminal window, Azure Cloud Shell, to avoid differences between operating systems and personal configurations. 

Open the Azure Cloud Shell which is located on the top navigation bar with the following icon >_

## 2. Clone the Workshop Git Repository

Clone the following GitHub repo into the Cloud Shell to get local access to the workshop demo files

```
git clone https://github.com/apprenda/hands-on-with-kubernetes-azure 
```

If you type `ls` into the command line you should see a new `hands-on-with-kubernetes-azure` directory. 

Change into the workshop directory you just cloned

```
cd hands-on-with-kubernetes-azure
```

## 3. Provision a Cluster

Run the following command to create a 3-node Kubernetes cluster in the Azure Container Service (ACS). This may take a minute to respond and will run for several minutes while the cluster is provisioned.

NOTE: In order to not go over the free tier limits, we are only provisioning 1 agent node. 

```
az group create --name myResourceGroup --location eastus2
``` 

```
az acs create --orchestrator-type kubernetes --resource-group myResourceGroup --name myK8s --agent-count 1 --generate-ssh-keys
```

When the command is finished executing, you will see a JSON output with your cluster information.

## 4. Connect To The Cluster

The following command downloads your Kubernetes credentials and configures kubectl (the Kubernetes CLI) to use them.

```
az acs kubernetes get-credentials --resource-group=myResourceGroup --name=myK8s
```

Now verify that `kubectl` can connect to the cluster

```
kubectl cluster-info
```

In order to access the Kubernetes dashboard via the Internet, we need to update it's configuration from NodePort to LoadBalancer. Edit the Service configuration by running the following command to open the definition, then change the Type from NodePort to LoadBalancer, save and exit. 

```
kubectl edit services/kubernetes-dashboard -n kube-system
```

After the change has been applied, run the following command until the External IP has a value (instead of pending). This command will watch the result and output any changes (it may take some time). Once the IP has been populated, hit Ctrl + C to exit the watch. 

```
kubectl get svc kubernetes-dashboard -n kube-system --watch
```

Open your browser and go to http://EXTERNALIP to see the Dashboard for your Cluster. 

## 5. Tour of Dashboard (the official UI of Kubernetes)

Instructor will give a tour of the Kubernetes Dashboard and cover the constructs of Kubernetes. 

They will then cover the demo apps found here https://github.com/apprenda/hands-on-with-kubernetes-azure/tree/master/docs/demos
