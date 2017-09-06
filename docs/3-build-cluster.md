# Build the Kubernetes Cluster

In this section, you will find code blocks with commands  for you to copy & paste into the command line interface of your choice. We have excluded the command prompt itself (the dollar sign `$`) from the snippets. 

**Tips for those who have not used a command line in ages**

It may take few minutes for a command prompt to respond. However, if it ever gets stuck you can use `Ctrl+C` to interrupt the current command and get back to the command prompt. 

You can use the `Up Arrow` to navigate to previous commands in the command history. 

To copy from the terminal window, simply highlight the desired text and it will be auto-copied. You can then use paste it as usual.

## 1. Sign In To Azure

For this workshop we will use the Azure CLI 2.0.  Here are the directions to install for your operating system: https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest  

To verify the download worked correctly, type az in the command line and you should see a help screen response.

Run the following command to login
```
az login
```
Copy the link from the response into a browser and enter in the authentication token (also in the response).

You will then be asked to enter in credentials after you enter the code in the browser - use the account you created earlier.

## 2. Clone the Workshop Git Repository

Go back to the command line and clone the following GitHub repo into the folder of your choice to get local access to the workshop demo files

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

NOTE: If you signed up using a token from a Microsoft representative you may have to use a different location.

NOTE: Here is link that shows the list of supported regions that can use the Container Service: https://azure.microsoft.com/en-us/regions/services/

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

In order to access the Kubernetes dashboard via the Internet, we need to run a proxy from your machine. You will need to open another command line window after this step becuause it will continue to run as long as you want to access the kubernetes ui.  

NOTE: This is currently a limitation of the Azure Container Service as we are not allowed to edit the service configuration for the kubernetes ui directly.

```
kubectl proxy
```

Open your browser and go to http://localhost:8001/ui to see the Dashboard for your Cluster. 

## 5. Tour of Dashboard (the official UI of Kubernetes)

Instructor will give a tour of the Kubernetes Dashboard and cover the constructs of Kubernetes. 

They will then cover the demo apps found here https://github.com/apprenda/hands-on-with-kubernetes-azure/tree/master/docs/demos

Reference for joining a kubernetes cluster via ACS: https://docs.microsoft.com/en-us/azure/container-service/kubernetes/container-service-connect#connect-to-a-kubernetes-cluster
