# Authenticating inside the cluster.
<hr/>
This example shows how to configure a client with client-go authenticate to the Kubernetes API from an application running inside the Kubernetes cluster.

client-go uses the Service Account token mounted inside the Pod at the `/var/run/secrets/kubernetes.io/serviceaccount` path when the `rest.InClsterConfig()` is used.

## Running this example
<hr/>
First compile the application for Linux:

```
GOOS=linux go build -i /app .
```
Then package it to a docker image using the provided Dockerfile to run it on Kubernetes.

If you are not using Minikube, you should build this image and push it to a registry that your Kubernetes cluster can pull from.   
If you have RBAC enabled on your cluster, use the following snippet to create role binding which will grant the default service account view permissions.
```
kubectl craete clusterrolebinding default-view --clusterrole=view --serviceacount=default:default
```
Then, run the image in a Pod with a single instance Deployment:
```
kubectl run --rm -i deom --image=in-cluster

There are 4 pods in the cluster
There are 4 pods in the cluster
...
```
The example now runs on Kubernetes API and successfully queries the number of pods in the cluster ever 10 seconds.
