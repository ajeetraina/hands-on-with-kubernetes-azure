# Secrets Demo Workflow

Secrets are a way to store sensitive information in Kubernetes.

The relevant Kubernetes documentation is found [here](https://kubernetes.io/docs/concepts/configuration/secret/)

These steps are to be executed in the Azure Cloud Shell. 

## 1. Navigate to the Workshop Directory (if necessary)  

```
cd hands-on-with-kubernetes-azure
```

## 2. Deploy a Kubernetes Secret

```
kubectl apply -f examples/secrets/app-secret.yaml
```

## 3. Deploy a Pod the Reference the Secret

```
kubectl apply -f examples/secrets/pod-with-secret.yaml
```

## 4. Locate the Pod

```
kubectl get pods -o wide
```

You should now see

```
NAME              READY     STATUS    RESTARTS   AGE       IP               NODE
secret-test-pod   1/1       Running   0          13s       172.16.235.215   k8s-agent-d7ca55cc-0
```

## 5. Obtain the Logs From the Pod

```
kubectl logs secret-test-pod
```

You should now see:

```
hello steven your password is randompassword
hello steven your password is randompassword
hello steven your password is randompassword
hello steven your password is randompassword
```

## 6. Delete the Demo

Finally execute the following command to tidy away the demo:

```
kubectl delete -f examples/secrets/app-secret.yaml
kubectl delete -f examples/secrets/pod-with-secret.yaml
```
