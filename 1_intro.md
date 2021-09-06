Kubernetes is a container orchestrator.

Orchestration is a process where containers are deployed managed, scaled, load balanced in a group.

There are similar tools to kubernetes like docker swarm and mesos.

Orchestration will protect the app from harware failures as there are many instances of the app.

User traffic can be managed by load balancing.

## Architecture

### Node

Is a machine. Physical or virtual on which k8 is installed. Containers will be launeched inside the node

### Master

Node witch k8 installed in it. Watches other nodes in the cluster and is responsible for the orchestration.

i.e one server can become a master and another a slave

### Components of k8

- API server - frontend of the k8. Interaction with cluster
- etcd - key-value store. Stores informations on the containers in the cluster.

- kubelet - agent that runs on each node in the cluster.

- container runtime - software used to run containers. I.E. docker

- controller - brain - noticing and responding when a container goes down.

- scheduler - distrubuting workload. Looks for newly created containers and assigned them the work.

## master vs slave components

master node will have components like

- kube-apiserver - for interfacing
- etcd
- controller
- scheduler

Slave node will have components like:

- kublet agent - for controlling the node
- runetime

# kubectl

tool for managing and controlling appilcations with command line, get cluster information, get status of nodes in the cluster.

kubectl run <app> - deploys app
kubectl cluster-info - gets information on the cluster
kubectl get node - get all nodes that are part of the cluster
