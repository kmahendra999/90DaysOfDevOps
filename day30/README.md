## Day 30 Task: Kubernetes Architecture

<p  align="center"><img  align="center"  src="https://kubernetes.io/images/kubernetes-horizontal-color.png"  /></p>

## Kubernetes Overview

With the widespread adoption of [containers](https://cloud.google.com/containers) among organizations, Kubernetes, the container-centric management software, has become a standard to deploy and operate containerized applications and is one of the most important parts of DevOps.

Originally developed at Google and released as open-source in 2014. Kubernetes builds on 15 years of running Google's containerized workloads and the valuable contributions from the open-source community. Inspired by Google’s internal cluster management system, [Borg](https://research.google.com/pubs/pub43438.html),

## Tasks

1. What is Kubernetes? Write in your own words and why do we call it k8s?

2. What are the benefits of using k8s?

3. Explain the architecture of Kubernetes, refer to [this video](https://youtu.be/FqfoDUhzyDo)

![1_HHRp0HENvfAu2hXT8Gto9g](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/df6e97f1-26ae-43f1-90ac-befd8180e960)

4. What is Control Plane?

5. Write the difference between kubectl and kubelets.

6. Explain the role of the API server.


<pre>
  1. What is Kubernetes (K8s)? Why is it called K8s?

Kubernetes is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications. It provides a framework for automating the deployment, scaling, and operation of application containers across clusters of hosts. The name "Kubernetes" is derived from Greek, meaning "helmsman" or "pilot," reflecting its role in steering and managing containerized applications.

The term "K8s" is a shorthand notation where "8" represents the eight letters between "K" and "s" in "Kubernetes."

  2. Benefits of using Kubernetes:

Container Orchestration: Efficiently manages the deployment and scaling of containerized applications.
Portability: Ensures consistency and portability across different environments, reducing compatibility issues.
Scalability: Easily scales applications up or down based on demand, optimizing resource utilization.
Automated Load Balancing: Distributes network traffic across multiple containers to ensure optimal performance.
Self-healing: Automatically replaces failed containers or reschedules workloads to maintain system health.
Declarative Configuration: Allows defining the desired state of the application, automatically adjusting to changes.
Resource Efficiency: Maximizes the use of underlying hardware resources through efficient container management.
Community Support: Active open-source community contributes to continuous improvement and innovation.

  3. Architecture of Kubernetes:

The architecture of Kubernetes is based on a master-node model. The master node manages the cluster, while worker nodes host the running applications. Key components include the API server, etcd, Controller Manager, Scheduler, and Kubelet.

  



  4. What is Control Plane?

The control plane in Kubernetes is the central management entity responsible for regulating the state of the cluster. It consists of several components, including the API server, Controller Manager, Scheduler, and etcd. The control plane makes decisions about the cluster's desired state based on API server input, continuously working to maintain the cluster in the desired configuration.

  5. Difference between kubectl and kubelet:

kubectl: This is the Kubernetes command-line tool used for interacting with the Kubernetes cluster. Developers and administrators use kubectl to deploy applications, inspect and manage cluster resources, and perform various administrative tasks.

kubelet: The kubelet is an agent running on each worker node in the cluster. It communicates with the API server and ensures that containers are running in a Pod. It takes care of starting, stopping, and maintaining application containers based on the Pod specifications provided by the control plane.


  6.  Role of the API server:

The API server is a central component of the Kubernetes control plane. It serves as the primary interface for all interactions with the cluster, receiving and processing requests from kubectl, kubelet, and other Kubernetes components. The API server validates and processes these requests, ensuring that the cluster stays in the desired state. It exposes the Kubernetes API, allowing users to manage and control the entire system. The API server is a key component for the declarative configuration of the cluster and the coordination of activities among various components.
  
</pre>

Kubernetes architecture is important, so make sure you spend a day understanding it. [This video](https://youtu.be/FqfoDUhzyDo) will surely help you.

_Happy Learning :)_

[← Previous Day](../day29/README.md) | [Next Day →](../day31/README.md)


<pre>
  Install K8

  on master and workers
*****************************************
Ip need to collect from aws portal so we can connect using short names
=========================================
with root
=========================================
sudo yum install -y vim-enhanced wget

cat <<EOF | sudo tee /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
3.82.187.188 master ip-172-31-83-234.ec2.internal
3.85.159.54 worker1 ip-172-31-81-232.ec2.internal
3.86.148.53 worker2 ip-172-31-81-226.ec2.internal
EOF

swapoff -a
systemctl disable firewalld
systemctl stop firewalld
setenforce 0

sed -i "s/^SELINUX=enforcing/SELINUX=disabled/" /etc/sysconfig/selinux

useradd admin
echo -e "redhat\nredhat" | passwd admin
echo "admin ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers.d/admin

sudo su admin

=========================================
with admin user
=========================================
cd ~

echo 'PATH=$PATH:/usr/sbin:/sbin' >> ~/.bashrc
source ~/.bashrc


sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine


sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

sudo yum install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo systemctl enable --now docker

cat <<EOF "| sudo tee" /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.29/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.29/rpm/repodata/repomd.xml.key
exclude=kubelet kubeadm kubectl cri-tools kubernetes-cni
EOF

sudo yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes
sudo systemctl enable --now kubelet

=========================================
only on master
=========================================

sudo kubeadm init --pod-network-cidr=10.244.0.0/16 

got error :
---------------------------------
WARNING Firewalkld]: firewalld is active, please ensure ports [6443 10250] are open or your cluster may not function correctly
error execution phase preflight: [preflight] 

Some fatal errors occurred: [ERROR CRI]: container runtime is not running Status from runtime service failed” err=”rpc error: code = Unimplemented desc = unknown service runtime.v1alpha2.RuntimeService”
---------------------------------
sudo rm /etc/containerd/config.toml
sudo systemctl restart containerd

sudo kubeadm init --pod-network-cidr=10.244.0.0/16 


on successfull installetion :
````````````````````````````````````````````````
on master To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

sudo kubeadm join 172.31.83.234:6443 --token bg6amc.41fohlpkftxs55mu --discovery-token-ca-cert-hash sha256:ef76427bfa3eebee90ca135e2f99a52363858336f603c5b6585e28fafbb0c9f2
[admin@ip-172-31-83-234 ~]$
````````````````````````````````````````````````

=========================================
only on worker
=========================================
sudo kubeadm join 172.31.83.234:6443 --token bg6amc.41fohlpkftxs55mu --discovery-token-ca-cert-hash sha256:ef76427bfa3eebee90ca135e2f99a52363858336f603c5b6585e28fafbb0c9f2


</pre>
