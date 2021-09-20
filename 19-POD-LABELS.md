How to create kubectl alias (optional):
- `alias k=kubectl`

Documentation:
- https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/

Add two labels on a POD:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx-labels-pod
    labels:
      environment: production
      app: nginx
  spec:
    containers:
    - name: nginx
      image: nginx:1.14.2
      ports:
      - containerPort: 80`
   ```
   
Get Pods by labels:
- `k get pods -l environment=production,tier=frontend`
