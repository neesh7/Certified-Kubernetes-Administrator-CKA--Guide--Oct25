# Deployments-Commands

#### **Reference links:** 
#### Deployment Documentation: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
#### K8 Cheatsheet: https://kubernetes.io/docs/reference/kubectl/quick-reference/

## **Deployments in Brief**: 
A Deployment manages a set of Pods to run an application workload, usually one that doesn't maintain state. Deployment automatically. Deployments are reffered as **deplpoy** in short.

To create a Deployment, we can **use commands directly** or you can **use a YAML file** like this and then **apply it** with **kubectl**:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80

```
Once Yaml file is ready as per need use this command to apply this yaml file to create replicasets.
```bash 
kubectl apply -f my-deployment.yaml
```

## Commands
### Basic kubectl commands
```bash
# Note - Setting shorthand for kubectl
$ alias k=kubectl

# create a deployment
$ kubectl create deployment --image=nginx nginx
$ kubectl create deployment --image=nginx nginx --dry-run=client -o yaml

$ kubectl create deployment --image=nginx nginx -n <your-namespace>


$ kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > my-deployment.yaml

# Generate Deployment with 4 Replicas

$ kubectl create deployment nginx --image=nginx --replicas=4
# create deployment using yaml manifest files

$ kubectl create -f rs-deployment.yml
$ kubectl apply -f rs-deployment.yml
$ kubectl get deploy 

# List Deployments

$ kubectl get deploy
$ kubectl get deploy -n <your-namespace>

# Delete Deployments

$ kubectl delete deploy <deploy-name>


$ kubectl replace -f replicaset-def.yml

# Scaling a replicaset
$ kubectl scale --replicas=6 replicaset-def.yml
$ kubectl scale --replicas=6 replicaset <Name-of-replicaset>

# we can also scale using edit command it will open live configuration file for us which we can update and our rs will be updated.

$ kubectl edit deploy <your-deployment>

# Debugging

$ kubectl describe deploy <deploymentName>
$ kubectl describe deploy --help
$ kubectl explain deploy