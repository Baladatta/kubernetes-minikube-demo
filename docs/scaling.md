# Scaling

This doc shows how to scale the Deployment in the demo.

Manual scaling:

```bash
kubectl scale deployment nodejs-deployment --replicas=4 -n devops-demo
kubectl get pods -n devops-demo
```

Horizontal Pod Autoscaling (example):

```bash
kubectl autoscale deployment nodejs-deployment --cpu-percent=50 --min=2 --max=10 -n devops-demo
kubectl get hpa -n devops-demo
```

Notes:
- Ensure resource `requests.cpu` is set for HPA to work with CPU metrics.
