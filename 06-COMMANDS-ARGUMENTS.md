How to create kubectl alias (optional):
- `alias k=kubectl`

Run POD with command and arguments:
  ```
  apiVersion: v1 
  kind: Pod 
  metadata:
    name: ubuntu-sleeper
  spec:
    containers:
    - name: ubuntu
      image: ubuntu
      command: ["sleep"]
      args: ["5000"]
  ```

  ```
  apiVersion: v1 
  kind: Pod 
  metadata:
    name: ubuntu-sleeper
  spec:
    containers:
    - name: ubuntu
      image: ubuntu
      command: 
        - "sleep"
        - "5000"
  ```

Obs.:
- The tag `command` is will overwrite the tag `ENTRYPOINT` from Dockerfile.
- The tag `args` is will overwrite the tag `CMD` from Dockerfile.

To see more details of the a POD:
- `k get po -o wide`