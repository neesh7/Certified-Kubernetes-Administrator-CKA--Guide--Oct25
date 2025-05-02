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

# to see the status of scheduler pod check kube-system namespace
$ kubectl get all -n kube-system

$ kubectl get po -o wide
