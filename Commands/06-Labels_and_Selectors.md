## Commands
### Basic kubectl commands
```bash
# Note - Setting shorthand for kubectl
$ alias k=kubectl

# use help
$ kubectl get po --help
# some shorthand
$ kubectl get po -l env=prod
$ kubectl get all -l env=prod,tier=front-end

# listing a POD based on label
$ kubectl get pods --selector env # lists all pod with this key in label
$ kubectl get pods --selector env=dev
$ kubectl get pods --selector env=dev --no-headers | wc -l
$ kubectl get alls --selector env=dev --no-headers | wc -l
$ kubectl get all --selector env=prod,bu=finance,tier=frontend
# Labelling a Node
$ kubectl label nodes <node-name> <label-key>=<label-value>
$ kubectl label nodes node-1 size=large
```
