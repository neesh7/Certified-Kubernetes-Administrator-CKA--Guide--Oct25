## Commands
### Basic kubectl commands
```bash
# Note - Setting shorthand for kubectl
$ alias k=kubectl

# listing a POD based on label
$ kubectl get pods --selector env
$ kubectl get pods --selector env:dev

# Labelling a Node
$ kubectl label nodes <node-name> <label-key>=<label-value>
$ kubectl label nodes node-1 size=large
```
