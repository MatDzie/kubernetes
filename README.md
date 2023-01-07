# Kubernetes learning

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

## Kubernetes commands:
- kubectl create -f fileName
- kubectl apply -f fileName (updates running pod/replicaset/deployment/service)
- kubectl delete pod/replicaset/deployment/service name
- kubectl get pods/replicaset/deployment/service
- kubectl describe pods/replicaset/deployment/service
- kubectl exec -it podName -c containerName -- /bin/bash (connects to conteiner with terminal)
- kubectl logs podName -c containerName (displays standard output from container)

## Knowledge base:
- Pod

    Pods are the smallest, most basic deployable objects in Kubernetes. A Pod represents a single instance of a running process in your cluster. Pods contain one or more containers, such as Docker containers. When a Pod runs multiple containers, the containers are managed as a single entity and share the Pod's resources.

- ReplicaSet

    A ReplicaSet (RS) is a Kubernetes object used to maintain a stable set of replicated pods running within a cluster at any given time.

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