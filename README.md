# k8s-practice

```
                 KUBERNETES CLUSTER
                        │
          ┌─────────────┴─────────────┐
          │                           │
     CONTROL PLANE                WORKER NODES
                                      │
                         ┌────────────┼────────────┐
                         │            │            │
                       Node 1       Node 2       Node 3
                         │            │            │
                       Pods         Pods         Pods
                         │            │            │
                         └────────────┼────────────┘
                                      │
                                Containers
                                      │
                                Application
                                      │
                                  Service
                                      │
                                   Users
```

- Node IP = where the machine is.
- Pod IP = where the application workload is inside the cluster.
- Service IP = stable address used to reach a group of Pods.

---
![Kubernetes Architecture](images/k8s_arc_tec.png)

## k8s-cmds

![Kubernetes Architecture](images/k8s_cmd.png)

Install the ingress-nginx controller:
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

Install the metrics-server (needed for HPA):
```
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

## HPA_VPA_KDA
![K8s](images/HPA_VPA_KDA.png)

