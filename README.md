# kubernetes-cluster
Multi node kubernetes-cluster which can be used for Certified Kubernetes Administrator training

[Certified Kubernetes Administrator ](https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/)


![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/3/39/Kubernetes_logo_without_workmark.svg/1200px-Kubernetes_logo_without_workmark.svg.png "Kubernetes")


### Prerequisites
- Vagrant should be installed on your machine.
- Oracle VirtualBox can be used as a Vagrant provider or make use of similar providers as described in Vagrant’s official documentation.
- Ansible should be installed in your machine. Refer to the Ansible installation guide for platform specific installation.

This playbook will be install the following packages, and then adding a user named “vagrant” to the “docker” group. 

- docker-ce
- docker-ce-cli
- containerd.io

Kubelet will not start if the system has swap enabled, so we are disabling swap using the below code.
Installing kubelet, kubeadm and kubectl using the below code.
 Initialize the Kubernetes cluster with kubeadm using the below code (applicable only on master node).
 Setup the kube config file for the vagrant user to access the Kubernetes cluster using the below code.

	Accessing master
	$ vagrant ssh k8s-master
	
	$ ## Accessing nodes
	$ vagrant ssh node-1
	$ vagrant ssh node-2
	
	vagrant@k8s-master:~$ kubectl get nodes
	NAME         STATUS   ROLES    AGE     VERSION
	k8s-master   Ready    master   18m     v1.13.3
	node-1       Ready    <none>   12m     v1.13.3
	node-2       Ready    <none>   6m22s   v1.13.3

## kube/config
Log into the k8s-master and run following commando for generating .kube/config file for external management:
kubectl config view --flatten --minify > /home/vagrant/cluster-cert.txt


Source:
<https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/>



