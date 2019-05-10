# Part 9: Manifest files

## Pods

A YAML manifest file to deploy a pod usually contains the following parts:

The main 4 top-level resources:
  - __apiVersion:__ defines which version of the K8s API to use
  - __kind:__ specifies which kind of object to deploy
  - __metadata:__ provides additional information about the object (for example, its name, namespace, labels...)
  - __spec:__ the spec provides nested information about the object that we are deploying (for example, what container/s to use, which ports...)
<br/>

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    env: dev
    version: v0.1
spec:
  containers:
  - name: hello-world
    image: hello-world:latest
    ports:
      - containerPort: 8080
```

When we are ready to deploy our manifest, we can just `create` or `apply` the file with `kubectl`:

```
$ kubectl create -f pod.yml
```
<br/>

## Replication Controller

A YAML manifest file to deploy a Replication Controller is very similar to the one used by the pod. It will also contain the 4 top-level resources we saw for the Pod, but its `spec` might differ.

Some fields used for the RC spec are:
  - __replicas:__ specifies how many pod replicas we want
  - __selector:__ defines which are the pods we want to target (we can select these by name, app, labels, etc)
  - __template:__ specifies the template we want to use for the pods, which would be similar to the fields we added in the `pod.yml` manifest
<br/>

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: hello-replication
spec:
  replicas: 5
  selector:
    app: hello-world-app
  template:
    metadata:
      labels: 
        app: hello-world-app
    spec:
      containers:
      - name: hello-world
        image: hello-world:latest
        ports:
          - containerPort: 8080
```
