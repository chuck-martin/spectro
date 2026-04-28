# Debug Operations in Kubernetes
Kubernetes includes several commands to help you debug:

 - `kubectl get pods [--namespace <name>]`
 - `kubectl logs <name>`
 - `kubectl exec <name>`
 - `kubectl debug <name`

|Use This Command| To Do This |
|--|--|
| `kubectl get pods [--namespace <name>]` | Get available pod names to pass to the `logs`, `exec`, and `debug` commands |
|`kubectl logs <name>`|Retrieve pod logs|
|`kubectl exec <name>`|Explore in a container|
|`kubectl debug <name>`|Clone a pod|


**Note:** All CLI commands used to interact with the Kubernetes API server begin with `kubectl` .
## `kubectl get pods [--namespace <name>]`
Lists information about all available pods, where `pods` is the resource passed to the `get` command, and `--namespace <name>` is an optional flag (see below). The information about available pods is returned as a table and includes:
 - Name - The name of the pod.
 - Ready - The ratio of ready containers in the pod to the total number of containers in the pod
 - Status - The current status of the pod, which can include Running, Pending, Waiting, or Terminated.
 - Restarts - The total number of container restarts in the pod.
 - Age - The amount of time since pod creation.

### Namespaces
A namespace defines and names a logical virtual cluster within a physical cluster. The `kubectl get pods` command returns information only about pods in the default namespace. Add the `namespace` flag to look into a specific environment. For example, `kubectl get pods --namespace production`.

For detailed information about the `get` command, see the [Kubernetes documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get).


## kubectl logs
Retrieves the logs of all containers in a pod. 
## kubectl exec
Allows exploration of the inside of a container.
## kubectl debug
Creates a clone of a pod that does not terminate if an error occurs within the container.





Kubernetes contains several commands, sometimes we can use these commands to do things. A good command to know is kubectl get pods which is used to get a list of all pods that are available and what their status is. Just rememember that when you use this command tat you may have to specify the `namespace`.

```shell
kubectl get pods --namespace 
```

Speaking of commands, kubectl is the CLI that is used to interact with k8s. The kubectl cli commmunicates with the kubernettes API server.  Another command that is helpful is the kubectl logs command. In Azure, kubernetess is available, just like other cloud providers. This command is used to retrive the logs of a specific pod - do use this when you have to review logs or need to debug a container. Another we will dicuss is the `kubectl exec` command. A command that we can use to debug a container from the inside or to explore the the enviroment of the container itself.  I recommend when debugging you start with kubectl get pods, then `kubectl logs` and lastly we can use `kubectl exec` to explore the inside of the container and review other log files or configurations. 

**Note:** The command `kubectl debug` is another option to considering when debugging a container. This command can be used to create a clone of a pod that does not terminate if an error is experienced inside the container. 



# References

- https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#-strong-getting-started-strong-

- [What is Kubernetes](https://kubernetes.io/docs/concepts/overview/)
