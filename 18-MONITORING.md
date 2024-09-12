
Go to github and install metrics-server(If needed):
- `https://github.com/kubernetes-sigs/metrics-server`

Get Nodes metrics:
- `k top nodes`

Get Pods metrics:
- `k top pods -n default`

Order results:
- `k top pods -n default --sort-by=cpu`
- `k top pods -n default --sort-by=memory`
