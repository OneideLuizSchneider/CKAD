How to create kubectl alias (optional):
- `alias k=kubectl`

Deployment Strategys:
- Recreate
- Rolling Update (Default)

Commands:
- `k apply -f deployment.yml`
- `k get deployments`
- `k set image deployment/nginx-deploy nginx=nginx:1.9.1`
- `k rollout status deployment/nginx-deploy`
- `k rollout undo deployment/nginx-deploy`
- `k rollout history deployment/nginx-deploy`

Deployment example:
  ```
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: nginx-deploy
    labels:
      app: app1
  spec:
    replicas: 2
    selector:
      matchLabels:
        app: app1
    template:
      metadata:
        labels:
          app: app1
      spec:    
        containers:
        - image: nginx:1.9.0
          name: nginx
  ```
