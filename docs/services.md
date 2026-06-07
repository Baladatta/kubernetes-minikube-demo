# Services

Service types explained:

- ClusterIP — internal cluster access (default).
- NodePort — exposes a static port on each node (used in this demo).
- LoadBalancer — external load balancer (cloud providers).

In this repo `service.yaml` uses `NodePort` with `nodePort: 30080` so you can access the app via `minikube ip:30080`.
