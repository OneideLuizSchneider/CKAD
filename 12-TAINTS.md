How to create kubectl alias (optional):
- `alias k=kubectl`

Create a taint
- `k taint nodes node-name key=value:taint-effect`
Example:
- `k taint nodes node1 app=ssd:NoSchedule`

Add Taint Tolerations on a POD:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx-pod
  spec:
    containers:
    - image: nginx
      name: nginx-container
    tolerations:
    - key: "app"
      operator: "Equal"
      value: "ssd"
      effect: "NoSchedule"
  ```

Or just on ControlPlane:
  ```
  tolerations:
  - key: "node-role.kubernetes.io/master"
    operator: "Exists"
    effect: "NoSchedule"
  ``` 

Remove a taint from a Node:
- `kubectl taint nodes controlplane node-role.kubernetes.io/master:NoSchedule-`

To see more details of the a POD:
- `k get po -o wide`