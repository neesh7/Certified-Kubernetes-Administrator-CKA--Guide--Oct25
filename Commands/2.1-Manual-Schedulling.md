## Manual Schedulling 

to manually schedule a pod over a particular node we can provide **nodeName** property in pod manifest yaml file.

```yaml

---
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  nodeName: node01
  containers:
  -  image: nginx
     name: nginx
```

$ kubectl get nodes
$ kubectl get po

#### to see the status of scheduler pod check kube-system namespace
$ kubectl get all -n kube-system

$ kubectl get po -o wide

#### Note: it is not possible to update node of a running pod and if we try to do it we need to first delete the running pod and create it back again with new node details. basically update the yaml manifest of pod-defination with new node details and run the below command.
$ kubectl replace --force -f pod-defination.yml

#### Note: while creating pods if we don't provide this nodename property in yaml file the pod is created based on schedulling algo to any available node which is kind of random. let's say later on we wish to update the node for pod. But there is no way to update node for running pod. In such case we can using k8's binding objects and send a post request to k8's binding api to update the node for already running pod.

```yaml

apiversion: v1
kind: Binding
metadata:
  name: nginx
target:
  apiversion: v1
  kind: Node
  name: node01
```
Convert the above yaml to equivalent json and send post request to binding api of k8
