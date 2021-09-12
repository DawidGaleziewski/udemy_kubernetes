controllers are the 'brain' of the k8. They monitor objects and respond to changes.

## Replication controllers

when POD crashes. Replicatopm controller will create a instance of the pod
.

Also used by load balancing and scaling

## Replica set

new recomanded way to set up replication

## definition file

Just like with pods we need a definition file for replication controller

rc-definition.yml

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: myapp-rc
  labels:
    type: front-end
spec:
  # template of the pod. Same as definition yaml of the pod but we do not need things like apiVersion. Therefore we nested two definition files
  template:
    metadata:
    name: my-awesome-app
    labels:
      app: myapp
      type: front-end
    spec:
    containers:
      - name: nginx-container
        image: nginx
    # same level as template. Siblings
   replicas: 3
```

## creating a replication controller

kubectl create -f ./file.yml

## get replication controllers

kubectl get replicationcontroller

# REPLICASET

replicaset is a bit diffrent

```yaml
## must be apps/v*
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myapp-rc
  labels:
    type: front-end
spec:
  template:
    metadata:
      name: my-awesome-app
      labels:
        app: myapp
        type: front-end
    spec:
      containers:
        - name: nginx-container
          image: nginx
  replicas: 3
  # new field when compare to replication controller. Replica set can also manage pods that were not created via its definition
  selector:
    matchLabels:
      type: front-end
```

creating replicaset and listing it

```bash
kubectl create -f replicaset-definition/yml
kubectl get replicaset
```

## labels and selectors

Role of replica set is to look at existing pods, by their label. And deploy a new one if they would fail.

It is a process that monitors pods.
There may be thousends of pods in the cluster. That is why replica set needs a label to find and monitor.

## why template?

it is used in case one of the pods would fail in the future and would have to be created once more

## updating replica sets

1. Update the definition file
2. Run kubectl
   kubectl replace -f replicaset-definition.yml

# what happens when we create more replicas then replicaSet is set to

k8 will terminate the extra pod we just created. k8 wont allow more pods with certain label then specified in replicaset definition file
