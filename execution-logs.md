# Execution Logs (sample outputs)

These are sample outputs you might see when running the demo commands locally.

## minikube start

```text
😄  minikube v1.30.1 on Microsoft Windows 10
✨  Using the hypervisor: Hyper-V
💡  Starting control plane node minikube in cluster minikube
🔥  Creating docker container (CPUs=2, Memory=2200MB) ...
🚜  Preparing Kubernetes v1.26.0 on Docker 20.10.8 ...
🏄  Done! kubectl is now configured to use "minikube" cluster
```

## kubectl get nodes

```text
NAME       STATUS   ROLES    AGE   VERSION
minikube   Ready    control-plane   2m    v1.26.0
```

## kubectl apply -f namespace.yaml

```text
namespace/devops-demo created
```

## kubectl apply -f deployment.yaml

```text
deployment.apps/nodejs-deployment created
```

## kubectl apply -f service.yaml

```text
service/nodejs-service created
```

## kubectl get pods

```text
NAME                                    READY   STATUS    RESTARTS   AGE
nodejs-deployment-5d8f7d6b7c-abc12      1/1     Running   0          1m
nodejs-deployment-5d8f7d6b7c-def34      1/1     Running   0          1m
```

## kubectl get services

```text
NAME            TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
nodejs-service  NodePort   10.96.123.45    <none>        80:30080/TCP   1m
kubernetes      ClusterIP  10.96.0.1       <none>        443/TCP        3m
```

## kubectl scale deployment nodejs-deployment --replicas=4

```text
deployment.apps/nodejs-deployment scaled
```

## kubectl describe pod

```text
Name:         nodejs-deployment-5d8f7d6b7c-abc12
Namespace:    devops-demo
Containers:
  nginx:
    Image:      nginx:latest
    Port:       80/TCP
    State:      Running
    Ready:      True
    RestartCount: 0
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  2m     default-scheduler  Successfully assigned devops-demo/nodejs-deployment-5d8f7d6b7c-abc12 to minikube
```

## kubectl delete service

```text
service "nodejs-service" deleted
```

## kubectl delete deployment

```text
deployment.apps "nodejs-deployment" deleted
```
