## **Service in Brief**: 
In Kubernetes, a Service is a method for exposing a network application that is running as one or more Pods in your cluster. Service are reffered as **svc** in short.Basically it's way to expose your application running inside a pod to external world so user can access it.

To create a Service, we can **use commands directly** or you can **use a YAML file** like this and then **apply it** with **kubectl**:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app.kubernetes.io/name: MyApp
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9376

```
Once Yaml file is ready as per need use this command to apply this yaml file to create replicasets.
```bash 
kubectl apply -f my-service.yaml
```

```bash
$ kubectl get svc
$ kubectl get svc -o wide
$ kubectl describe svc <servicename>
$ kubectl get service --help

# Creating a service using commands
$ kubectl expose deployment <deployment-name> --type=<service-type> --name=<service-name> --port=<port> --target-port=<target-port>

# example
$ kubectl expose deployment my-deployment --type=LoadBalancer --name=my-service --port=80 --target-port=8080

# Task - 
# Create a new service to access the web application using the service-definition-1.yaml file.



# Name: webapp-service
# Type: NodePort
# targetPort: 8080
# port: 8080
# nodePort: 30080
# selector:
#   name: simple-webapp

# kubectl expose command indeed doesn't support the --node-port flag directly. Instead, you can create the Service first and then patch it to add the nodePort

# expose deployment without specifying node port
$ kubectl expose deployment simple-webapp-deployment --name=webapp-service --type=NodePort --port=8080 --target-port=8080
# Patch the node-port now
$ kubectl patch service webapp-service -p '{"spec":{"ports":[{"port":8080,"targetPort":8080,"nodePort":30080}]}}'

```