# Kubernetes Learning Repo

## minikube
A lightweight Kubernetes implementation that creates a VM on your local machine and deploys a simple cluster containing only one node.

https://minikube.sigs.k8s.io/docs/start/

## VSC Plugins:
- Kubernetes
- Kubernetes Support
- Non-breaking spaces
- YAML
- Dev Containers
- Docker

## Kubernetes useful commands:
- kubectl create -f fileName
- kubectl apply -f fileName
- kubectl delete 'kind' objectName
- kubectl get 'kind'
- kubectl describe 'kind'

- kubectl exec -it podName -c containerName -- /bin/bash (connects to container with terminal)
- kubectl logs podName -c containerName (displays standard output from container)
- kubectl get 'kind' objectName -o yaml > newFile.yaml (writes object to .yaml)
- kubectl edit 'kind' objectName (opens running object configuration in editor allowing for changes on the fly, it will open the editor defined by your KUBE_EDITOR)
- kubectl top 'kind' (see CPU and memory usage of object)

https://kubernetes.io/docs/reference/kubectl/cheatsheet/

## Key concepts:
- Node

    A node is the smallest unit of computing hardware. It is a representation of a single machine in your cluster. In most production systems, a node will likely be either a physical machine in a datacenter, or virtual machine hosted on a cloud provider.

- Cluster

    A cluster is a set of nodes that run containerized applications.

- Pod

    Pods are the smallest, most basic deployable objects in Kubernetes. A Pod represents a single instance of a running process in your cluster. Pods contain one or more containers, such as Docker containers. When a Pod runs multiple containers, the containers are managed as a single entity and share the Pod's resources.

- ReplicaSet

    A ReplicaSet (RS) is object used to maintain a stable set of replicated pods running within a cluster at any given time.

- Deployment

    A Kubernetes Deployment tells Kubernetes how to create or modify instances of the pods that hold a containerized application. Deployments can help to efficiently scale the number of replica pods, enable the rollout of updated code in a controlled manner, or roll back to an earlier deployment version if necessary.

- How do Pods communicate in Kubernetes? 

    K8s create internal virtual network which is accessable inside the cluster. Each Pod gets an cluster IP address (10.x.x.x). 
    
    Best way to talk to Pods is by creating ClusterIP service which will create enpoints for them.

    Generic endpoint format: service-name.namespace-name.svc.cluster.domain

- How can we communicate with a Pod from outside of K8s?

    There are three different services to communicate with a Pod: LoadBalancer (used when platform supports it and its needed for trafic managment), Ingress (most popular option), and NodePort (shouldn't be used on production, highly unsecure).

    Service can be viewed as routing record, it's not an actual running process.

- Namespace

    Namespaces are used to separate concerns in k8s. We create them with kind:Namesace and to put some object into given namespace we define it in object metadata as namespace: namespace-name.

- Persistent Volumes (PV)

    Way of making storage availble inside k8s. Used with EBS (Elastic Block Storage - virtual hard drive) on AWS for example. To name them we use Storage Class Names.

 - Persistent Volume Claims (PVC)

    Way of saying that I want a chunk of that storage to use it.

- Static vs Dynamic Storage Classes

    Static: we as administrator have to create Persistent Volumes, manage it.
    Dynamic: we delegate job for creating and managment to k8s.

- ConfigMaps

    A ConfigMap is an API object used to store non-confidential data in key-value pairs. Pods can consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a volume.

    A ConfigMap allows you to decouple environment-specific configuration from your container images, so that your applications are easily portable.

- Secret

    A Secret is an object that contains a small amount of sensitive data such as a password, a token, or a key. Such information might otherwise be put in a Pod specification or in a container image. Using a Secret means that you don't need to include confidential data in your application code.

