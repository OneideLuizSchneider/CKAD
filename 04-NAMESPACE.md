How to create kubectl alias (optional):
- `alias k=kubectl`

List all namespaces:
- `k get ns`

Create a namespace
- `k create ns mynamespace`

Create a pod in a specific namspace
- `k run redis --image=redis -n mynamespace`

To see more details of the a POD:
- `k get po -o wide`