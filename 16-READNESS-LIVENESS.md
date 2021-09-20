How to create kubectl alias (optional):
- `alias k=kubectl`

Add livenessProbe and readinessProbe on a POD:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx-pod
  spec:
    containers:
    - image: nginx
      name: nginx-container
      livenessProbe:
        httpGet:
          path: /ready
          port: 80
        initialDelaySeconds: 5
        timeoutSeconds: 2
      readinessProbe:
        httpGet:
          path: /ready
          port: 80
        initialDelaySeconds: 5
        timeoutSeconds: 2
        periodSeconds: 1
  ```
