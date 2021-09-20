How to create kubectl alias (optional):
- `alias k=kubectl`

Get Nodes metrics:
- `k get pods --selector app=app1`

Add a Label on a POD:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx-pod
    labels:
      app: app1
  spec:
    replicas: 1
    selector:
      matchLabels:
        app: app1
    template:
      metadata:
        labels:
          app: app1
      spec:    
        containers:
        - image: nginx
          name: nginx-container
  ```

Get all objects with an label:
- `k get all --selector env=prod -A`
Get all objects with more then one label:
- `k get pod --selector env=prod,type=nginx,node=worker1`
