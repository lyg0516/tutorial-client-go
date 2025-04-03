# Create, Update & Delete Deployment

This example program demonstrates the fundamental operations for managing on Deployment resources, such as `Create`, `List`, `Update`, and `Delete`.   
You can adopt the source code from this example to write programs that manage other types of resources through the Kubernetes API.  

## Running this example
Make sure you have a Kubernetes cluster and `kubectl` is configured:
```
kubectl get nodes
```
Compile this example on your workstation:
```
cd create-update-delete-deployment
go build -o ./app
```
Now, run this application on your workstation with your local kubeconfig file:
```
./app
# or specify a kubeconfig file with flag
./app -kubeconfig=$HOME/.kube/config
```
Running this command will execute the following operations on your cluster:
1. Create Deployment: This will create a 2 replica Deployment. 
2. Update Deployment: This will update the Deployment resource created in previous step by setting the replica
count to 1 and changing the container image to `nginx:1.13`. You are encouraged to inspect the retry loop that handles conflicts. Verify the new replica
count and container image with `kubectl describe deployment demo`
3. List Deployment: This will retrieve Deployments in the `default` namespace and print their names and replica counts.
4. Delete Deployment: This will delete the Deployment object and its dependent ReplicaSet resource. 

Each step is separated by an interactive prompt. You must hit the `Return` key to proceed to the next step.
You can use these prompt as a break to time to run `kubectl` and inspect the result of the operations executed.
