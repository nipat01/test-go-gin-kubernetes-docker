# Go(Gin) deploy docker container to Kubernertes on localhost
## Installation


```sh
git clone this project
download docker desktop => https://docs.docker.com/desktop/windows/install/ 
after donwloaded go to setting => kubernetes then check the box Enable Kubernetes
download Minikube => https://minikube.sigs.k8s.io/docs/start/
```




## Usage

start minikube (It takes a long time for the first):
```sh
minikube start
```
```sh
kubectl apply -f k8s-deployment.yml
```
output: "deployment.apps/go-gin-kubernetes created"

get deployment:

```sh
kubectl get deployments
```
get pods:

```sh
kubectl get pods
```
output:
go-gin-kubernetes-fcb7c54f9-6wmgj   1/1     Running   0          12m
go-gin-kubernetes-fcb7c54f9-h46p5   1/1     Running   0          12m
go-gin-kubernetes-fcb7c54f9-j4q5c   1/1     Running   0          12m

get service:
```sh
kubectl get services
```
output:
NAME                     TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
go-hello-world-service   NodePort    10.107.38.130   <none>        9090:30165/TCP   5m29s


access to each pod using this command
```sh
kubectl port-forward go-gin-kubernetes-fcb7c54f9-6wmgj 8080:8080
curl localhost:8080
```
access url service in the minikube using this command
```sh
minikube service go-hello-world-service --url
```
output:
| NAMESPACE |          NAME          | TARGET PORT |          URL           |
|-----------|------------------------|-------------|------------------------|
| default   | go-hello-world-service |             | http://127.0.0.1:55718 |

stop minikube
```sh
minikube stop
```

