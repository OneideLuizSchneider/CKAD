How to create kubectl alias (optional):
- `alias k=kubectl`

Create a label
- `k label nodes node1 app=ssd`

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
    nodeSelector:
      app: ssd
  ```

Remove a taint from a Node:
- `kubectl taint nodes controlplane node-role.kubernetes.io/master:NoSchedule-`

To see more details of the a POD:
- `k get po -o wide`