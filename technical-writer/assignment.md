# Debug Operations in Kubernetes
Kubernetes includes several commands to help you debug:

|Use This Command| To Do This |
|--|--|
| `kubectl get pods [--namespace <namespace-name>]` | Get available pod names to pass to the `logs`, `exec`, and `debug` commands |
|`kubectl logs <pod-name>`|Retrieve pod logs|
|`kubectl&nbsp;exec&nbsp;<pod-name>&nbsp;[-c&nbsp;<container-name>]&nbsp;--&nbsp;<command>`|Explore in a container|
|`kubectl debug <pod-name>`|Create a cloned pod specifically configured for debugging|


**Note:** All CLI commands used to interact with the Kubernetes API server begin with `kubectl` .
## `kubectl get pods [--namespace <namespace-name>]`
Lists information about all available pods, where `pods` is the resource passed to the `get` command, and `--namespace <name>` is an optional flag (see below). The information about available pods is returned as a table and includes:
 - Name - The name of the pod.
 - Ready - The ratio of ready containers in the pod to the total number of containers in the pod.
 - Status - The current status of the pod, which can include Running, Pending, Waiting, or Terminated.
 - Restarts - The total number of container restarts in the pod.
 - Age - The amount of time since pod creation.

### Namespaces
A namespace defines and names a logical virtual cluster within a physical cluster. The `kubectl get pods` command returns information only about pods in the default namespace. Add the `namespace` flag to look into a specific environment. For example, `kubectl get pods --namespace production`.

For detailed information about the `get` command, see the [Kubernetes documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get).


## `kubectl logs <pod-name>`
Retrieves the logs of all containers in a pod, where `pod-name` is the resource passed to the `logs` command. 

This can provide information about pod behavior, including crashes or errors without needing to log in to the pod.

For detailed information about the `logs` command, see the [Kubernetes documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#logs).
## `kubectl exec <pod-name> [-c <container-name>] -- <command>`
Allows exploration of the inside of a container by executing commands directly inside the container. The double-dash (`--`) separates the kubectl command from the command you want to run inside the container. If you do not specify a container name, the command will use the default or first container in the pod.

For detailed information about the `exec` command, see the [Kubernetes documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#exec).
### Examples
`kubectl exec -it <pod-name> -- /bin/bash` - Opens an interactive shell in the default container.

`kubectl exec <pod-name> -- env` - Checks the environmental variables in the default container.

`kubectl exec <pod-name> -- cat /etc/config/settings.yaml` - Views the contents of the `etc/config/settings.yaml` file in the default container.
## `kubectl debug <pod-name>`
Creates a temporary container clone in an existing pod to run diagnostic tools or a clone of a target pod with modified attributes to troubleshoot startup crashes. The `debug` command also provides automation for common debugging tasks.

For detailed information about the `debug` command, see the [Kubernetes documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#debug).

## Additional References
- [Kubernetes overview](https://kubernetes.io/docs/concepts/overview/)
- [Kubernetes getting started](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#-strong-getting-started-strong-)

