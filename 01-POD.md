How to create kubectl alias (optional):
- `alias k=kubectl`

Pod alias:
- `k get pod mypod`
- `k get pods mypod`
- `k get po mypod`

Get pods with aditional details:
- `k get pods -o wide`

Create a pod
- `k run nginx --image=nginx`

Describe pod
- `k describe pod nginx`

Delete pod
- `k delete pod nginx`

Create pod with generated yml
- `k run redis --image=redis123 --dry-run=true -o yaml > redis.yaml`
- `k run --generator=run-pod/v1 --image=reid123 redis --dry-run --env=foo=bar -o yaml > redis.yml`
- `k run --generator=run-pod/v1 --image=reid123 redis --dry-run -o yaml > redis.yml`

If you don't have de definition you can run:
- `k get pod <pod-name> -o yaml > pod-definition.yaml`
You can as well edit the pod definitions:
- `k edit pod <pod-name>`

Create and expose a POD on port 8080:
- `k run custom-nginx --image=nginx --port=8080`

To see more details of the a POD:
- `k get po -o wide`