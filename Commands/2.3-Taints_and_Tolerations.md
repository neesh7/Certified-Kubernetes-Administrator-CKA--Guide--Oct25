## **Taints and Tolerations in Brief**: 
Basically taint and toleration is well thought mechanism to make sure only eligible pods get assigned to a node. we basically taint a node (it's like marking a node) and pods which have tolerations ( similar marking) to the node can be placed on the node.


## Commands
### Basic kubectl commands
```bash
# Note - Setting shorthand for kubectl
$ alias k=kubectl

# Checking a node have taint or not

$ kubectl describe node <node-name> 

# tainting a node 
$ kubectl taint --help
$ kubectl taint node <node-name> key=value:effect

# Removing a taint
$ kubectl taint nodes controlplane node-role.kubernetes.io/control-plane:NoSchedule-
```
#### whenever we schedule a pod, why it never gets schedulled on control plane ?
#### Because master node have taint on it which restricts any random pod to be scheduled on it.
$ kubectl describe node kubemaster | grep Taints
