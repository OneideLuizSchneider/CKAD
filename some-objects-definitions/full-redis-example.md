Create deployment:
- `kubectl create deployment redis --image=redis:alpine --replicas=1`
  
Expose Deployment:
- `kubectl expose deployment redis --name=redis --port=6379 --target-port=6379`
  
Create a Ingress NetworkPolicy for the label redis:
```
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: redis-access
  namespace: default
spec:
  podSelector:
    matchLabels:
       app: redis
  policyTypes:
  - Ingress
  ingress:
  - from:
    - podSelector:
        matchLabels:
          access: redis
    ports:
     - protocol: TCP
       port: 6379
```
