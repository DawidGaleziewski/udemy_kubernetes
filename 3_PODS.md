We should have a Docker Image available at docker repository for kubernetes to be pulled down.

Kubernetes Cluster should be set up an already working.

K8 does not deploy containers directly at the worker nodes. Containers are encapsulated into k8 object.

k8 encapsulated containers are known as PODS. PODs can be looked on also as a instance of a aplication.
POD is a smallest object we can create in a kubernetes.

PODS are inside a worker node (virtual or physical machine).

When k8 scales aplication (ie during workload) iw will create a brand new POD with a instance of that app.

node: {POD1:{Container}, POD2:{Container}}

Also kubernetes can scale by deploying a pod on a new node, if the previous one runs out of computing power.

PODs have a 1 to 1 relation with the container and the instance of the application.

To scale up, we create new PODs, to scale down we delete existing PODs.

Single POD can have a multiple containers. However they are not multiple containers of the same kind. I.E helper containers living alongside our app.

Containers can communicate by referring to each other via localhost as they share the same space.

# deploying pods.

kubectl run nginx --image nginx

it deploys docker container by creating a POD.
Creates a POD and deploys a instance of the image.
we need to specify the name of the image as well.

Image is downloaded from dockerhun repository.
k8 can be configured to pull off the image eaither from public repo or company repo.

we can see all PODs in cluster by running:

## geting information on our pods:

List all pods
kubectl get pods
kubectl get pods -o wide

Get details on a pod
kubectl describe pod nginx
