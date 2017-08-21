# dotnetcore Workflow

These steps are to be executed in the Azure Cloud Shell.

## 1. Navigate to your local repository directory

```
cd hands-on-with-kubernetes-azure
```

## 2. Execute the Kubernetes service and application deployment

```
kubectl apply -f examples/dotnetcore/service.yaml
kubectl apply -f examples/dotnetcore/deployment.yaml
```

## 3. Display the pods running which are serving our application

Execute the following command:

```
kubectl get pods -o wide
```

You should now see

```
NAME                                READY     STATUS              RESTARTS   AGE       IP        NODE
dotnetcorek8s-v1-3306003563-1ntbq   0/1       ContainerCreating   0          23s       <none>    k8s-agent-d7ca55cc-0
dotnetcorek8s-v1-3306003563-33f25   0/1       ContainerCreating   0          23s       <none>    k8s-agent-d7ca55cc-0
dotnetcorek8s-v1-3306003563-q6c07   0/1       ContainerCreating   0          23s       <none>    k8s-agent-d7ca55cc-0
```

## 4. Obtain the public IP and port of the service

```
$ kubectl get services
```

You should now be seeing:

```
NAME               CLUSTER-IP    EXTERNAL-IP    PORT(S)        AGE
dotnetcorek8s-lb   10.0.26.154   40.79.72.179   80:30713/TCP   1m
kubernetes         10.0.0.1      <none>         443/TCP        1h
```

## 5. Browse to the website

*GET*

Now from your browser browse to `http://<public ip>/api/hello`

Your browser will display "Hello!"

*POST*

The dotnetcore api also allows POST requests to this endpoint with a parameter called `myname`.
Add `?myname=YOURNAME` to the URL above and your browser will display "Ahoy there, YOURNAME!"


## 6. Delete the demo

Finally execute the following command to tidy away the demo:

```
kubectl delete -f examples/dotnetcore/service.yaml
kubectl delete -f examples/dotnetcore/deployment.yaml
```
