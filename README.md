# NodePort Service, Load Balancer Service, and Ingress

###  Create a Kubernetes Pod:
```
kubectl create -f cv-pod.yaml
```
output:
> pod/cv-pod created

### 1. Create NodePort Service:
```
kubectl create -f cv-services.yaml
```
output:
> service/cv-service created

**Type and running command to show url service**
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
### 2. Create LoadBalancer Service:

Create LoadBalancer same as we create NodePort the different is on Yaml service file we defined LoadBalancer type and get auto port

```
kubectl create -f cv-services-load-balancer.yaml
```
output:
> service/cv-service-load-balancer created

**Type and running command to show url service**
```
minikube service cv-service-load-balancer
```
Example output:
```
|-----------|--------------------------|-------------|-----------------------------|
| NAMESPACE |           NAME           | TARGET PORT |             URL             |
|-----------|--------------------------|-------------|-----------------------------|
| default   | cv-service-load-balancer |          80 | http://192.168.99.100:32053 |
|-----------|--------------------------|-------------|-----------------------------|
```
Opened up on browser based on url we get

### 3. Create Ingress Networking

Use **cv-service** we had before to use in Ingress file yaml

* Create the Ingress resource from yaml file by running the following command

```
kubectl create -f cv-ingress.yaml
```

Output:
```
ing.k8s.io/v1 Ingress
ingress.networking.k8s.io/cv-ingress created
```
* Setting Our hosts file (this example am us Ubuntu with vs code editor):

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

**Or running from browser**

