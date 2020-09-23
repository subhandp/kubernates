# 1 Set up Ingress

###  Create a Deployment:
```
kubectl create deployment cv --image=subhandp/tailwinddocker:latest
```
> output:
> deployment.apps/cv created

### Expose the Deployment:
```
kubectl expose deployment cv --type=NodePort --port=80
```
> output:
> service/cv exposed

### Verify the Service is created and is available on a node port:
```
kubectl get service cv
```

### Visit the service via NodePort:
```
minikube service cv --url
```

> example output:
> http://192.168.99.100:30183

### Create the Ingress resource by running the following command:
```
kubectl apply -f cv-ingress.yaml
```

### Verify that the Ingress controller is directing traffic:
```
curl subhandp.cv
```

** or running from browser**
