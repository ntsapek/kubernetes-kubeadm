# kubernetes-kubeadm
Create a Kubernetes cluster using kubeadm

We use an ansible playbook to automate the creation of a Kubernetes cluster consisting of one master and two worker nodes.
The details of the nodes are defined in the Vagrantfile and Virtualbox is being used as provider.

Start by typing:

```vagrant up```

After the completion of the playbook, login to the master node and check the status of the nodes:

```vagrant ssh master```


```vagrant@master:~$ kubectl get nodes```

```NAME     STATUS   ROLES    AGE     VERSION
master   Ready    master   21m     v1.9.1
node1    Ready    <none>   7m44s   v1.9.1
node2    Ready    <none>   4m43s   v1.9.1
```