
Limite resorces for all the PODS in default NS:
  ```
  apiVersion: v1
  kind: LimitRange
  metadata:
    name: mem-limit-range
  spec:
    limits:
    - default:
        memory: 512Mi
      defaultRequest:
        memory: 256Mi
      type: Container      
  ```

Limite resorces for a POD:
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
      resources:
        limits:
          memory: "1G"
          cpu: 1
        requests:
          memory: "512M"
          cpu: 100m
  ```

Obs.: The status OOMKilled indicates that it is failing because the pod ran out of memory.

To see more details of the a POD:
- `k get po -o wide`