How to create kubectl alias (optional):
- `alias k=kubectl`

Documentation:
- https://kubernetes.io/docs/concepts/services-networking/network-policies/

NetworkPolicy example:
  ```
  apiVersion: networking.k8s.io/v1
  kind: NetworkPolicy
  metadata:
    name: db-network-policy
    namespace: default
  spec:
    podSelector:
      matchLabels:
        role: db
    policyTypes:
    - Ingress
    ingress:
    - from:
      - namespaceSelector:
          matchLabels:
            project: mynamespace
      - podSelector:
          matchLabels:
            role: api-pod
      - ipBlock:
        cidr: 10.0.0.0/24
      ports:
      - protocol: TCP
        port: 5432
  ```

Create it:
- `k apply -f np-definition.yml`


Obs.: ***Flannel*** does not support NetwotkPolicies.
      But ***Kube-router, Calico, Romana, Weave-net*** does.
