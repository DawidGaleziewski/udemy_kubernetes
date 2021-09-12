We can eaither use cloud solution and install all components ourselfs or use minikube - solution to install k8 locally and play with it

# setup

## kubectl

we need to install kubectl. On windows need to download executable and put it in the PATH

will start comands with kubectl ...

## minikube

install with exe.

## staring minikube

Setup the driver:
minikube start --driver="virtualbox"

this will autocreate a vm

## checking status

minikube status

kubectl get nodes

## creating first deployment

kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
kubectl expose deployment hello-minikube --type=NodePort --port=8080

## get url of the exposed service

minikube service hello-minikube --url

we can see if the server is running on:
http://192.168.99.100:32439

## delete the service

kubectl delete service hello-minikube
