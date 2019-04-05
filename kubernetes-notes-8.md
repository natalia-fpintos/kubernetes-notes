# Part 6: Working with pods

## Pods and Containers

As we already saw, a pod is the _atomic unit_ of schedulling in Kubernetes.

All containers inside a pod will be sharing the same IP address, however they will be running in different ports. This IP defined in the pod is actually a __network namespace__ or `netns`.

This means the pod share a single:
- IP address
- localhost adapter
- Set of ports
- cgroup
- Volumes access
- Network access
- IPC namespaces

![Pod and Containers](./images/pod-and-containers.png)
<br/>

## Inter-pod communication

The IP address of each pods is routable, so when we create the __Pod Network__, pods are connected and can talk to each other.
<br/>

## Intra-pod communication

The containers inside a pod can communicate easily over the shared __localhost interface__. If they need to communicate with the outside, they can be exposed on specific ports (one by container). 
<br/>

## Replication Controller

The replication controller allows us to spin pods, by providing a __desired state__ in the manifest.
Kubernetes will run a __reconciliation loop__ in the background, which will make sure that the current state matches this desired state, and will make any amends in case it finds a mismatch (i.e. spinning a new pod if the desired state are 5 pods and we currently only have 4).
