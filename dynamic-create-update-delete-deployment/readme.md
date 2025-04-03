# Create, Update & Delete Deployment with the Dynamic Package
This example program demonstrates the fundamental operations for managing on Deployment resources. such as `Create`, `List`, `Update` and `Delete` using `dynamic` package.

## Typed VS Dynamic
The code in this directory is based on a similar example that uss Kubernetes typed client sets.
The typed client sets make it simple to communicate with the API server using pre-generated local API objects to achieve an RPC-like programming experience.
Typed clients uses program compilations to enforce data safety and some validation.
However, when using typed clients, programs are forced to be tightly coupled with the version and the types used.

The `dynamic` package on the other hand, uses a simple type. `unstructured.Unstructured`, to represent all object values from the API server.
Type `Unstructured` uses a collection of nested `map[string]interface{}` values to create an internal structure that closely resemble the REST payload from the server.

The dynamic package defers all data bindings until runtime. 
This means programs that use the dynamic client will not get any of the benefits of type validation until the program is running.
This may be a problem for certain types of applications that require strong data type check and validation.

Being loosely coupled, however, means that programs that uses the `dynamic` package do not require recompilation when the client API changes.
The client program has more flexibility in handing updates to the API surface without knowing ahead of time what those changes are.

## Running this example
```
./app -kubeconfig=$HOME/.kube/config
```