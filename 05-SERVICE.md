How to create kubectl alias (optional):
- `alias k=kubectl`

List all services:
- `k get svc`

View service definition before create it:
- `k create service clusterip nginx-service --tcp=80:80 --dry-run=client -o yaml`

Generate it:
- `k create service clusterip nginx-service --tcp=80:80 --dry-run=client -o yaml > svc-definition.yml`

Create it:
- `k aplly -f svc-definition.yml`

Expose a pod:
- `kubectl expose pod nginx --port=80 --name nginx-service --type=ClusterIP`

To see more details of the a POD:
- `k get po -o wide`