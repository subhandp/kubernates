# NodePort Service, Load Balancer Service, and Ingress

###  Create a Kubernetes Pod:
```
kubectl create -f cv-pod.yaml
```
> output:
> pod/cv-pod created

### 1. Create NodePort Service:
```
kubectl create -f cv-services.yaml
```
> output:
> service/cv-service created

**Type and run to show url service**
```
minikube service cv-service
```
Example output:
```
|-----------|------------|-------------|-----------------------------|
| NAMESPACE |    NAME    | TARGET PORT |             URL             |
|-----------|------------|-------------|-----------------------------|
| default   | cv-service |          80 | http://192.168.99.100:30036 |
|-----------|------------|-------------|-----------------------------|
```
### 1. Create LoadBalancer Service:

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
> ingress.networking.k8s.io/cv-ingress created

### Setting Our hosts file (this example is on Ubuntu using vs code editor):
- **First, because we use Minikube get external ip**
> minikube ip
- **Next, setting hosts file using my minikube ip**
> code /etc/hosts
- **add line (Ip is example depend on your computer)**
> 192.168.99.100 subhandp.cv

### Verify that the Ingress controller is directing traffic:
```
curl subhandp.cv
```

**or running from browser**

