How to create kubectl alias (optional):
- `alias k=kubectl`

Create Secret based on a Yaml file:
- To encode de values run this command:
- `echo -n 'user' | base64`
- `echo -n 'pass' | base64`
  ```
  apiVersion: v1 
  kind: Secret 
  metadata:
    name: secret-example
  data
    DB_USER: "dXNlcg=="
    DB_PASS: "cGFzcw=="
  ```
- `k apply -f secret.yml`

- To decode:
- `echo -n 'dXNlcg==' | base64 --decode`
- `echo -n 'cGFzcw==' | base64 --decode`
  
Or:

- `k create secret generic secret-example --from-literal=DB_USER=user --from-literal=DB_PASS=pass`
To show the secret above:
- `k get secret secret-example -o yaml`
  
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
        - secretRef:
            name: secret-example
  ```
- `k apply -f confimap.yml`  

To see more details of the a POD:
- `k get po -o wide`