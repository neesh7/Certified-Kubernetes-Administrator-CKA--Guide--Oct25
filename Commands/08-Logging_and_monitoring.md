## Commands
### Basic kubectl commands
```bash
# Note - Setting shorthand for kubectl
$ alias k=kubectl

# Cloning Metrics Server
https://github.com/kubernetes-sigs/metrics-server
$ git clone https://github.com/kodekloudhub/kubernetes-metrics-server.git

#  Once Cloned, use below command to install the metrics-server binary
$ kubectl create -f kubernetes-metrics-server/

# View data of Nodes or Pods using Metrics-Server
$ kubectl top node
$ kubectl top pod

# Tracking Application logs

# for a pod with single container
$ kubectl logs -f <pod-name>

# for a pod with multiple container, we must specify the name of container too
$ kubectl logs -f <pod-name> <container-name1>
```
