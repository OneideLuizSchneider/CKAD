How to create kubectl alias (optional):
- `alias k=kubectl`

Create configMaps based with a Yaml file:
  ```
  apiVersion: v1 
  kind: ConfigMap 
  metadata:
    name: cm-example
  data
    VAR_1: "value1"
    VAR_2: "value2"
  ```
- `k apply -f confimap.yml`
  
Or:

- `k create cm cm-example generic --from-literal=VAR_1=value1 --from-literal=VAR_2=value2`
  
Use it:
  ```
  apiVersion: v1 
  kind: Pod 
  metadata:
    name: mypod
  spec:
    containers:
    - name: mypod
      image: nginx
      envFrom:
        - configMapRef:
            name: cm-example
  ```
- `k apply -f confimap.yml`  

To see more details of the a POD:
- `k get po -o wide`