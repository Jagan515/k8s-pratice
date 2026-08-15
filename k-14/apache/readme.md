## HPA Stress Test — Step-by-Step Commands

### 1. Check Apache Pods

```bash
kubectl get pods -n apache
```

### 2. Check HPA

```bash
kubectl get hpa -n apache
```

### 3. Check current CPU

```bash
kubectl top pods -n apache
```

### 4. Check HPA details

```bash
kubectl describe hpa apache-hpa -n apache
```

### 5. Start CPU stress test

```bash
kubectl run cpu-load -n apache --image=busybox --restart=Never -- /bin/sh -c 'while true; do :; done'
```

### 6. Check stress Pod

```bash
kubectl get pods -n apache
```

### 7. Check CPU again

```bash
kubectl top pods -n apache
```

### 8. Watch HPA

```bash
kubectl get hpa -n apache -w
```

### 9. Watch Apache Pods

```bash
kubectl get pods -n apache -w
```

**Important:** The `cpu-load` Pod itself consumes CPU; it does **not** directly cause `apache-hpa` to scale because the HPA targets `apache-deployment`. For a true Apache HPA test, the CPU load must occur inside the Pods managed by `apache-deployment`.

### 10. Stop the stress test

```bash
kubectl delete pod cpu-load -n apache
```

### 11. Check CPU after stopping

```bash
kubectl top pods -n apache
```

### 12. Watch HPA scale down

```bash
kubectl get hpa -n apache -w
```

### 13. Watch Pods scale down

```bash
kubectl get pods -n apache -w
```

### 14. Check final HPA state

```bash
kubectl describe hpa apache-hpa -n apache
```

### 15. Verify only the minimum replicas remain

```bash
kubectl get deployment apache-deployment -n apache
```

### 16. If you want to delete the HPA

```bash
kubectl delete hpa apache-hpa -n apache
```

### 17. If you want to delete the Apache application

```bash
kubectl delete deployment apache-deployment -n apache
```

### 18. Delete the Service

```bash
kubectl delete service apache-service -n apache
```

### 19. Delete the Namespace

```bash
kubectl delete namespace apache
```

**For your current HPA lab, steps 1–14 are enough.** Don't run steps 16–19 unless you actually want to remove the resources.
