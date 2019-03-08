# Part 5C: Manual installation of K8s

## Manual install with _kubeadm_

- We need 3 machines (for example AWS EC2 instances) with the following installed:
  * Docker
  * Kubelet
  * Kubeadm
  * Kubectl
  * CNI - Container Network Interface

Once installed, we can run the following command on the node we have decided will be the master, this will create a single-node cluster on the machine:

```
$ kubeadm init
```

Then, we do a bit of config with the following commands:

```
$ sudo cp /etc/kubernetes/admin.conf $HOME/
$ sudo chown $(id -u):$(id -g) $HOME/
$ export KUBECONFIG=$HOME/admin.conf
```

After this, we should be able to see our nodes and pods with `kubectl`. However, until we add a __pod network__ these won't show as ready:

```
$ kubectl apply --filename https://git.io/weave-kube-1.6
```

After its creation, we should be able to log into the other node machines and make them join the cluster using the command provided by `kubeadm` during the creation of the cluster. This command looks like this:

```
$ kubeadm join --token 67dc9sjk.rknjdv89876ejda 127.0.0.0:1234
```
