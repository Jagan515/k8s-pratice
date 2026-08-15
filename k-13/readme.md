# Taints & Tolerations

Taints go on **nodes** and repel pods. Tolerations go on **pods** and let them
be scheduled onto nodes with a matching taint. A toleration doesn't force a
pod onto a tainted node — it only permits it; use `nodeAffinity` /
`nodeSelector` alongside it if the pod must land there.

## Taint effects

- `NoSchedule` — new pods without a matching toleration won't be scheduled here.
- `PreferNoSchedule` — the scheduler tries to avoid it, but it's not a hard rule.
- `NoExecute` — new pods are kept off, and existing pods without the toleration are evicted.

## Try it

Taint a worker node:
```
kubectl taint nodes tws-cluster-worker3 dedicated=special:NoSchedule
```

Apply the pod (has a matching toleration in `pod.yml`) and confirm it lands
on the tainted node:
```
kubectl apply -f pod.yml
kubectl get pod toleration-demo-pod -o wide
```

Remove the taint when done:
```
kubectl taint nodes tws-cluster-worker3 dedicated=special:NoSchedule-
```
