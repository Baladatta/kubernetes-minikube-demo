# kubernetes-minikube-demo

## Project Overview

This demo shows how to deploy and manage a simple Node.js-style app (served here via `nginx:latest` as a placeholder) on a local Kubernetes cluster using Minikube.

## Objective

Deploy a containerized application to Kubernetes (Minikube), expose it via a Service, and demonstrate scaling and basic management operations.

## Tools Used

- Minikube
- kubectl
- Docker (local image handling)
- Kubernetes (apps/v1, Service, Namespace)

## Kubernetes Architecture

- Namespace: isolates resources in `devops-demo`.
- Deployment: manages ReplicaSets and Pods (`nodejs-deployment`).
- Service: NodePort service (`nodejs-service`) exposing port 80 on node port 30080.

## Deployment Explanation

`deployment.yaml` defines a Deployment named `nodejs-deployment` with 2 replicas, using the `nginx:latest` image and exposing container port 80. It includes resource requests/limits and liveness/readiness probes.

## Service Explanation

`service.yaml` creates a `NodePort` Service named `nodejs-service` that maps port 80 to container port 80 and uses `nodePort: 30080` so the app is reachable on the Minikube node.

## Namespace Explanation

`namespace.yaml` creates a dedicated namespace `devops-demo` to isolate demo resources.

## Scaling Explanation

Use `kubectl scale deployment nodejs-deployment --replicas=<n> -n devops-demo` to change the number of replicas. The deployment will create or remove pods as needed. The `scaling.md` in `docs/` provides details.

## kubectl Commands

Examples used in this project:

```bash
minikube start
kubectl get nodes
kubectl apply -f namespace.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods -n devops-demo
kubectl get services -n devops-demo
kubectl scale deployment nodejs-deployment --replicas=4 -n devops-demo
kubectl describe pod <pod-name> -n devops-demo
kubectl delete service nodejs-service -n devops-demo
kubectl delete deployment nodejs-deployment -n devops-demo
```

## Folder Structure

```
kubernetes-minikube-demo/
│
├── deployment.yaml
├── service.yaml
├── namespace.yaml
├── execution-logs.md
├── README.md
├── .gitignore
│
├── docs/
│   ├── kubernetes-basics.md
   ├── scaling.md
   └── services.md
│
└── screenshots/
```

## Screenshots

Place screenshots from your Minikube dashboard or `kubectl` outputs in the `screenshots/` folder. Example files: `screenshots/minikube-start.png`.

## Conclusion

This repo provides a simple, production-minded starting point for learning Kubernetes on Minikube, covering deployment, service exposure, namespaces, and scaling.
