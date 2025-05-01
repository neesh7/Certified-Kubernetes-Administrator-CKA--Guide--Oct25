# Pod-Commands

#### **Reference links:** 
#### Pod Documentation: https://kubernetes.io/docs/concepts/workloads/pods/
#### K8 Cheatsheet: https://kubernetes.io/docs/reference/kubectl/quick-reference/

## **Pods in Brief**: 
Pods are the smallest, most basic deployable units in Kubernetes, encapsulating one or more containers that share storage, network, and a specification for how to run the containers.
###### **Pods Short form is **Po****

To create a Pod, we can **use commands directly** or you can **use a YAML file** like this and then **apply it** with **kubectl**:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: mycontainer
    image: myimage:latest
```
Once Yaml file is ready as per need use this command to apply this yaml file to create pods.
```bash 
kubectl apply -f my-pod.yaml
```

## Commands
### Basic kubectl commands
```bash
$ kubectl version
$ kubectl version --output=yaml
$ kubectl run hello-minikube
$ kubectl cluster-info
$ kubectl get nodes
$ kubectl get node -o wide
```
### Get Pod details

```bash
# Note - Setting shorthand for kubectl
$ alias k=kubectl

# List all pods
$ kubectl get pods
$ kubectl get pods --watch
$ kubectl get pods -o wide
$ kubectl get pods -o yaml

# kubectl command with verbosity levels 
# Kubernetes uses verbosity levels from 0 to 10:

-v=0: Normal user-level output (default).
-v=1 to 4: Increasingly detailed logs for typical troubleshooting.
-v=5 to 6: Shows HTTP requests/responses to the API server.
-v=7: Includes request and response headers, and some internal decision-making details.
-v=8+: Very detailed (e.g., includes full request/response bodies, deep internal logic).

$ kubectl get pods -v=7 and 9 is the max verbosity level


$ kubectl get pods --namespace <your-namespace>
$ kubectl get pods -n <your-namespace>
# Getting count of pods
$ kubectl get pods --no-header| wc -l

# Getting pods in controlplane
$ kubectl get pods -n kube-system
# Getting pods based on selector 
$ kubectl get pods --selector myapp=DjangoApp

# use of grep
$ kubectl get pods | grep "keyword"

# List all pods in all namespaces
$ kubectl get pods --all-namespaces
$ kubectl get pods -n

# Describe a pod
$ kubectl describe pod <podname>
$ kubectl explain pod
```

### Create/ update/ delete a Pod

```bash
# creates pod in default namespace
$ kubectl run <podname> --image <imagename> --sleep 1d
$ kubectl run redis --image=redis123 --dry-run=client -o yaml
$ kubectl run redis --image=redis123 --dry-run=client -o yaml > my-pod.yml

# creates Pod in targeted namespace
$ kubectl run <podname> --image <imagename> -n <your-namespace>

# creating pods and doing port mapping
$ kubectl run <podname> --image <imagename> --port <port like 8080>

# To generate a Yaml manifest quickly for pods, use dry run and redirection
$ kubectl run redis --image=redis123 --dry-run=client -o yaml > redis-definition.yaml

# Simply creating a Pod
$ kubectl run redis --image=redis

# creating pod with help of YAML file
$ kubectl apply -f <yaml>
$ kubectl create -f <yaml>

# Editing a Pod 
$ kubectl edit pod <pod name> 
$ kubectl exec -it webapp -- /bin/bash

# Deleteing a Pod
$ Kubectl delete pod <podname1> <podname2>

# Delete and create in single commands
$ kubectl prelace --force -f my-pod-yaml.yml

# to get help with a command
$ kubectl create pod --help
```

### Debugging a Pod or View Pod logs
```bash 
$ kubectl logs <podname>

# Stream Pod logs in real-time
$ kubectl logs -f <podname>

# Get a shell into a running container
$ kubectl exec -it <podname> -- /bin/bash
```

### Post Forwarding a Pod
```bash
# Forward a local port to a port on the Pod
$ kubectl port-forward <podname> <local-port>:<pod-port>
```

### Scaling a Pod
``` bash
# Scale the number of replicas in a deployment
$ kubectl scale deployment <deployment-name> --replicas=<number>
```
