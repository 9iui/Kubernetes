# Kubernetes
collection of all my k8 deployments for pods, services and ingress 


## Kubernetes Deployments and Ingress Configuration

This repository contains the necessary files and configurations for deploying applications using Kubernetes, along with the steps to set up an Ingress for routing traffic to these applications.

### Deployment Commands

To deploy your application using Kubernetes, follow these steps:

1. **Clone the Repository**: Clone this repository to your local machine using the following command:
## random notes 

different between pod clusters node 

-helm 

container orchestration 
micro services 

pods - smallest unit 
nodes -0
worker node -A physical or virtual server  
pod - smallest unit of kubernete 

communicate through services ...pods 

check out putting user names and password in kubernetes configmap 
secrets base64  

Deployments: how many pods and replica you want ... scale up or scale down 
blue print of my-app pod 

statfulset for databases ...replicating the pods and increase n memory ...reduce inconsistency 



- Ingress: A Kubernetes Ingress is an API object that provides external access to services within a Kubernetes cluster. It acts as a reverse proxy and can route incoming traffic to the appropriate Kubernetes services based on the URL.its also act as a dns for switching the service name to the external url name 
- Service: A Kubernetes Service is an abstraction layer that provides a stable IP address and DNS name for accessing a set of pods. It enables load balancing and service discovery among pods.
- ConfigMap: A Kubernetes ConfigMap is an API object that holds key-value pairs of configuration data that can be used by other Kubernetes objects such as pods, deployments, and services. it is also  the external config to your application 
- Pod: A Kubernetes Pod is the smallest deployable unit in Kubernetes. It represents a single instance of a running process in a cluster, and can contain one or more containers. one application in  one pod 
- Volume: A Kubernetes Volume is a directory that can be accessed by a pod and its containers. It can be used to store data that needs to persist across pod restarts.
- Secrets: A Kubernetes Secret is an API object that holds sensitive information such as passwords, API keys, and certificates. It is encrypted at rest and can be used by other Kubernetes objects such as pods, deployments, and services.
- StatefulSet: A Kubernetes StatefulSet is a controller that manages the deployment of stateful applications such as databases. It ensures that each pod in the set is created and scaled in a specific order, and that each pod has a unique identity that persists across restarts.replication of databases 
- Deployment: A Kubernetes Deployment is a controller that manages the deployment of stateless applications such as web servers. It ensures that the desired number of replicas are running and can perform rolling updates and rollbacks.

k8s architecture 
master and slave nodes 
3 process installed on every node container runtime ,kubelet ,kube proxy 

Container Runtime:
A container runtime is a program responsible for running containers on a host system. It's an essential component of containerization, which allows developers to package applications and their dependencies into portable, isolated, and lightweight containers that can run consistently across different environments. Container runtimes provide the necessary environment and resources to run containers, such as namespaces, cgroups, and filesystems. Popular container runtimes include Docker, containerd, CRI-O, and rkt.

Kubelet:

Kubelet is a component of Kubernetes that runs on each node in the cluster and is responsible for managing and monitoring the containers running on that node. It communicates with the Kubernetes API server to receive instructions for pod creation, updates, and deletion. The kubelet ensures that the containers are running and healthy, and it restarts them if they fail. It also monitors the resource usage of the containers and reports back to the API server.

Kube Proxy:
Kube Proxy is another component of Kubernetes that runs on each node in the cluster and is responsible for network proxying. It handles the networking routing for Kubernetes services, allowing pods to communicate with each other across different nodes and exposing services to the outside world. Kube Proxy sets up rules in the host's firewall to forward traffic to the appropriate pods and services. It also supports load balancing and high availability features for services. Kube Proxy uses the IPtables or IPVS kernel modules to handle the network traffic routing.


master nodes /servers:
different processes running on the services 
api server,scheduler ,controller manager .etcd

API Server:
The API server is the central component of a Kubernetes cluster that exposes the Kubernetes API. It serves as the primary interface for managing the cluster and orchestrating the deployment, scaling, and management of containerized applications. The API server validates and processes incoming requests from kubectl, kubelet, kube-proxy, and other Kubernetes components. It stores the state of the cluster in etcd and communicates with the controller manager and scheduler to ensure the desired state of the cluster is maintained.

Scheduler:
The scheduler is responsible for distributing pods across the nodes in a Kubernetes cluster based on resource availability and other scheduling constraints. It monitors the API server for unscheduled pods and selects a suitable node for them to run on. The scheduler takes into account factors such as node availability, resource usage, affinity, anti-affinity, and node taints and tolerations when making scheduling decisions.

Controller Manager:
The controller manager is a Kubernetes component that runs multiple controllers responsible for maintaining the desired state of the cluster. Each controller is responsible for managing a specific aspect of the cluster, such as ReplicaSet, Deployment, DaemonSet, and StatefulSet controllers. The controller manager monitors the state of the cluster by querying the API server and reconciles any discrepancies by updating the desired state of the cluster.

etcd:
etcd is a distributed key-value store used by Kubernetes to store the state of the cluster. It provides a reliable, consistent, and highly available data store that can be used to store configuration data, cluster state, and other information. etcd stores the data in a hierarchical key-value format and supports features such as atomic updates, leases, and watches. The API server reads and writes data to etcd, and the controller manager and scheduler use it to maintain the desired state of the cluster.


minikube - this is a small production kubernete environment which uses one node to hosts the master and worker  in a virtual environment 
 kubectl - sends command tot he api server which is located in the master node  the workwr processis on minicube will crrate the pod , services and network , this is how it is used to communicate with the pode and worker nodes 


whats the differnce between the contol-plane and master role 

In Kubernetes, the control plane is the set of components that manage the Kubernetes cluster. The control plane includes the API server, etcd, the scheduler, and the controller manager. The control plane is responsible for accepting and processing API requests, scheduling pods on nodes, and maintaining the desired state of the cluster.

On the other hand, the master node is a term that is used in some Kubernetes documentation to refer to the node that runs the control plane components. However, the term "master" has been deprecated in favor of the more generic "control plane" term.

So in essence, the control plane and master node refer to the same thing - the set of components that manage the Kubernetes cluster. However, "control plane" is the preferred term to use in newer Kubernetes documentation and is consi

Some basic kubenetes commands 
kubectl is the command-line tool used to interact with a Kubernetes cluster. Here are some of the basic commands used in kubectl and a brief description of what they do:

kubectl get: Used to retrieve information about Kubernetes resources. The most common subcommands are get pods, get services, get deployments, and get nodes.

kubectl describe: Used to get more detailed information about a specific Kubernetes resource. For example, kubectl describe pod my-pod will provide detailed information about the specified pod.

kubectl create: Used to create a new Kubernetes resource. For example, kubectl create deployment my-deployment --image=my-image will create a new deployment using the specified image.

kubectl apply: Used to create or update a Kubernetes resource based on the configuration file. For example, kubectl apply -f my-config.yaml will apply the configuration in the specified file to the cluster.

kubectl delete: Used to delete a Kubernetes resource. For example, kubectl delete deployment my-deployment will delete the specified deployment.

kubectl logs: Used to view the logs of a specific pod. For example, kubectl logs my-pod will display the logs for the specified pod.

kubectl exec: Used to execute a command in a running container in a specific pod. For example, kubectl exec my-pod -- ls /app will execute the command ls /app in the specified pod.

These are just some of the basic kubectl commands, and there are many more available. You can get a full list of commands by running kubectl --help. Additionally, each command has many options and flags that can be used to customize the behavior of the command. You can get more information on a specific command by running kubectl <command> --help.


kuberentes configoration file 


```
kubectl create deployment nginx-depl --image=nginx -- creating a pod in kubernetes 
kubectl apply -
```

A Namespace is like a virtual cluster within a Kubernetes cluster. It provides a way to partition and isolate resources, such as pods, services, and volumes, from each other. Each Namespace has its own set of resources and policies that govern the access and usage of those resources.


3 parts of a kube deployment : metadata, specifications and status 
info about the pod and deployment is retrieved from the etcd and added tot he deployment file 






with miikube you can not start external service without using 
minikube service <service _name>

blue green depoyment: verison control  testing two versions 


what is ingress 

ingress deployment and ingress controller 