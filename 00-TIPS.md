## Usefull tips

Aliases:
- `alias k=kubectl`
- `alias kdr='kubectl -o yaml --dry-run=client'`
  
Usefull commands:
- `kubectl explain <RESOURCE TAG>`
- `kubectl -n default get events | grep -i "Any message"`
- `kubectl run -i --tty busybox --image=busybox --restart=Never -- sh`
- To run inside a Busybox image: `nc -v -w <TIME> <IP/HOST> <PORT>`