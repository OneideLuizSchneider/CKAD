How to create kubectl alias (optional):
- `alias k=kubectl`

List deployments:
- `k get deploy`

Describe deployment:
- `k describe deploy nginx-deploy`

Delete replicaset
- `k delete deploy nginx-deploy`

View a deployment before create it:
- `k create deploy nginx-deploy --image=nginx --replicas=1 --dry-run=client -o yaml`

Generate it:
- `k create deploy nginx-deploy --image=nginx --replicas=1 --dry-run=client -o yaml > nginx-deploy.yml`

Create it:
- `k apply -f nginx-deploy.yml`
