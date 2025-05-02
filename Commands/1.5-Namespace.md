## Namespace Commands

### Basic kubectl commands
```bash
# Note - Setting shorthand for kubectl
$ alias k=kubectl
$ kubectl get pods --all-namespace
$ kubectl get pods -A
$ kubectl get pods --namespace=kube-system
$ kubectl get pods -n kube-system
```
#### CreatePod in Particular Namespace
```bash
$ kubectl run pods mypod --image busybox -n dev
```

#### Other commands
```bash
# usually when we run any command it loads result from default namespace but we can update that to using this below command

# switching namespace
$ kubectl config set-contex $(kubectl config current-context) --namespace=dev
```
