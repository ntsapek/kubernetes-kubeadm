# kubernetes-kubeadm
Bootstrap a Kubernetes cluster.

An ansible playbook is used to automate the creation of a Kubernetes cluster via kubeadm. The cluster consists of one master and two worker nodes. The details of the nodes are defined in the Vagrantfile and Virtualbox is being used as vagrant provider.

Start by typing:

```$ vagrant up```

Wait for the playbook to finish and login to the master node to check the status of the rest:

```$ vagrant ssh master```


```$ vagrant@master:~$ kubectl get nodes```

```NAME     STATUS   ROLES    AGE     VERSION
master   Ready    master   21m     v1.9.1
node1    Ready    <none>   7m44s   v1.9.1
node2    Ready    <none>   4m43s   v1.9.1
```
