# Part 5: Installing K8s

## Minikube

Minikube allows us to try Kubernetes on our own computer, creating a local environment for our cluster.

When we start minikube, it creates and starts a VM on our machine, which spins up a single node K8s cluster. Then, it makes it available to the host machine, so we can control the cluster with `kubectl` as if the cluster was actually running on the machine instead of the VM.

![Minikube architecture](./images/minikube-architecture.png)

