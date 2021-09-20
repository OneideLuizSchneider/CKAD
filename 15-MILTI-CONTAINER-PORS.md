How to create kubectl alias (optional):
- `alias k=kubectl`

Add a Label on a POD:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx-pod
  spec:
    containers:
    - image: nginx
      name: nginx-container
    affinity:
      nodeAffinity:
        requiredDuringSchedulingIgnoredDuringExecution:
          nodeSelectorTerms:
          - matchExpressions:
            - key: app
              operator: In
              values:
              - ssd
  ```

To see more details of the a POD:
- `k get po -o wide`