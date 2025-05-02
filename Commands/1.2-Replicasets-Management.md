# Replicaset-Commands

#### **Reference links:** 
#### Replicaset Documentation: https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/
#### K8 Cheatsheet: https://kubernetes.io/docs/reference/kubectl/quick-reference/

## **ReplicaSets in Brief**: 
A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. Usually, you define a Deployment and let that Deployment manage ReplicaSets automatically. Replicaset are reffered as **rs** in short.

To create a Replicaset, we can **use commands directly** or you can **use a YAML file** like this and then **apply it** with **kubectl**:

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: frontend
  labels:
    app: guestbook
    tier: frontend
spec:
  # modify replicas according to your case
  replicas: 3
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: frontend
    spec:
      containers:
      - name: php-redis
        image: us-docker.pkg.dev/google-samples/containers/gke/gb-frontend:v5
```
Once Yaml file is ready as per need use this command to apply this yaml file to create replicasets.
```bash 
kubectl apply -f my-replicaset.yaml
```

## Commands
### Basic kubectl commands
```bash
# Note - Setting shorthand for kubectl
$ alias k=kubectl

# create a replicaset
$ kubectl create replicaset <replicasetname> --image=<image-name> --replicas=3 -n <your-namespace>


$ kubectl create replicaset my-replicaset --image=myimage:latest --replicas=3 --dry-run=client -o yaml > my-replicaset.yaml


$ kubectl create -f rs-defination.yml
$ kubectl apply -f rs-defination.yml
$ kubectl get rs 

# List replicasets

$ kubectl get replicaset
$ kubectl get replicaset -n <your-namespace>

# Delete Replicasets

$ kubectl delete rs <replicaset-name>

# The command $ kubectl replace -f replicaset-def.yml is used to update an existing ReplicaSet with a new configuration specified in the replicaset-def.yml file. It's like swapping out an old plan for a new one, making sure the cluster reflects the updated desired state.

$ kubectl replace -f replicaset-def.yml

# Scaling a replicaset
$ kubectl scale --replicas=6 replicaset-def.yml
$ kubectl scale --replicas=6 replicaset <Name-of-replicaset>

# we can also scale using edit command it will open live configuration file for us which we can update and our rs will be updated.

$ kubectl edit rs <your-replicaset>

# Debugging

$ kubectl describe rs <replicasetName>
$ kubectl describe rs --help
$ kubectl explain rs