#### Service

Service NodePort:
  ```
  apiVersion: v1
  kind: Service
  metadata:
    name: my-service
  spec:
    type: NodePort
    ports:
    - targetPort: 80
      port: 80
      nodePort: 30008
    selector:
      app: myapp    
  ```

Service ClusterIP:
  ```
  apiVersion: v1
  kind: Service
  metadata:
    name: my-service
  spec:
    type: ClusterIP
    ports:
    - targetPort: 80
      port: 80
    selector:
      app: myapp    
  ```

Create it:
- `k apply -f service-definition.yml`