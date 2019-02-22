# Course: Kubernetes 101

VMs vs Virtualised containers:
- Resources allocated to VMs are reserved for them, and not shared even if not in use.
- Containers only need the resources they are currently using, even if more are allocated to it, it can be used by different containers.

Kubernetes helps with some limitations of Docker:
- No horizontal scalling
- Lack of awareness of other containers running on different machines
- Cannot fix/re-spin a container if it fails or dies


etcd has a db with the state of the application service. This desired state is what the app constantly monitors to make sure the current state is correct (i.e. I should be running 3 containers but I only have one at the moment, I should spin 2 more).

The master node is managed by IBM cloud if you use their service.

