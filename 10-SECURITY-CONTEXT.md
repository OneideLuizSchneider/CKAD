
Security Context for the POD:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: ubuntu-sleeper
  spec:
    securityContext:
      runAsUser: 1000
    containers:
    - command:
      - sleep
      - "4800"
      image: ubuntu         
  ```

Security Context for the Container:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: ubuntu-sleeper
  spec:
    containers:
    - command:
      - sleep
      - "4800"
      image: ubuntu         
      securityContext:
        runAsUser: 1000
  ```

Security Context for the Container with capabilities:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: ubuntu-sleeper
  spec:
    containers:
    - command:
      - sleep
      - "4800"
      image: ubuntu         
      securityContext:
        runAsUser: 1000
        capabilities:
          add: ["SYS_TIME"]
  ```

To see more details of the a POD:
- `k get po -o wide`

---

Doc:
- <https://kubernetes.io/docs/tasks/configure-pod-container/security-context/>