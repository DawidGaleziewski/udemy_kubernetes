K8 uses yaml for deifing PODs.

Defintion always contains at least 4 fields that are root level properties

Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-awesome-app
  labels:
    app: myapp
    type: front-end
spec:
  containers:
    - name: nginx-container
    image: nginx
```

Variants

```yaml
apiVersion: v1 | apps/v1
kind: Pod | Service | ReplicaSet | Deployment
# data about the object
metadata:
  name: my-awesome-app
  labels:
    app: myapp
# Additional information depending on the kind of object
spec:
  containers:
    # dash shows this is a first item in the list. Item is a dictionary with two properties
    - name: nginx-container
      image: nginx
```

in order to create a pod from a kubectl

```bash
kubectl create -f pod-definition.yml
```

we can see the pods with:

kubectl get pods
