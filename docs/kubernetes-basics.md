# Kubernetes Basics

This document covers the basic Kubernetes concepts used in this demo.

- Pod: smallest deployable unit that runs one or more containers.
- Deployment: declarative way to manage Pods and ReplicaSets.
- Service: stable network endpoint to expose Pods.
- Namespace: virtual cluster to isolate resources.

Files in this repo:

- `namespace.yaml` — defines the `devops-demo` namespace.
- `deployment.yaml` — defines the Deployment and Pod template.
- `service.yaml` — exposes the pods via a NodePort Service.
