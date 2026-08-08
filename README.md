# k8s-pratice

                 KUBERNETES CLUSTER
                        │
          ┌─────────────┴─────────────┐
          │                           │
     CONTROL PLANE                WORKER NODES
                                      │
                         ┌────────────┼────────────┐
                         │            │            │
                       Node 1       Node 2       Node 3
                         │            │
                       Pods         Pods
                         │
                    Containers
                         │
                    Application
                         │
                      Service
                         │
                       Users

- Node IP = where the machine is.

- Pod IP = where the application workload is inside the cluster.

- Service IP = stable address used to reach a group of Pods.       

---
![Kubernetes Architecture](images/k8s_arc_tec.png)

# k8s-cmds 

![Kubernetes Architecture](images/k8s_cmd.png)


