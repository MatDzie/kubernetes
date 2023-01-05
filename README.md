# Kubernetes learning

## minikube - local Kubernetes
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
- kubectl apply -f fileName (updates running pod/replicaset/deployment)
- kubectl delete pod/replicaset/deployment name
- kubectl get pods/replicaset/deployment
- kubectl describe pods/replicaset/deployment
- kubectl exec -it podName -c containerName -- /bin/bash (connects to conteiner with terminal)
- kubectl logs podName -c containerName (displays standard output from container)