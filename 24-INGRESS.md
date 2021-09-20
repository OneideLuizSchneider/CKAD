How to create kubectl alias (optional):
- `alias k=kubectl`
- `alias kdr='kubectl -o yaml --dry-run=client'`
  
Install Nginx Ingress Controller Steps:
- ConfigMap
  - `kdr create configmap nginx-configuration -n ingress-space > configmap.yml`
- ServiceAccount
  - `kdr create sa ingress-serviceaccount -n ingress-space > sa.yml`

Nginx Ingress Controller:
  ```
  apiVersion: v1
  kind: ConfigMap
  metadata:
    name: ingress-nginx-controller  
  ---

  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: ingress-nginx-controller
  spec:
    selector:
      matchLabels:
        name: nginx-ingress-controller
    template:
      metadata:
        labels:
          name: nginx-ingress-controller
      spec:
        dnsPolicy: ClusterFirst
        containers:
          - name: nginx-controller
            image: quay.io/kubernetes-ingress-controller/nginx-ingress-controller:0.21.0
            imagePullPolicy: IfNotPresent
            args:
              - /nginx-ingress-controller
              - --publish-service=$(POD_NAMESPACE)/
            env:
              - name: POD_NAME
                valueFrom:
                  fieldRef:
                    fieldPath: metadata.name
              - name: POD_NAMESPACE
                valueFrom:
                  fieldRef:
                    fieldPath: metadata.namespace
            ports:
            - name: http
              containerPort: 80
              protocol: TCP
            - name: https
              containerPort: 443
              protocol: TCP

  ---

  apiVersion: v1
  kind: Service
  metadata:
    namespace: ingress-nginx
  spec:
    type: NodePort
    ports:
      - name: https
        port: 443
        targetPort: 443
        protocol: TCP
      - name: http
        port: 80
        targetPort: 80
        protocol: TCP
    selector:
      name: nginx-ingress-controller

  ---

  apiVersion: v1
  kind: ServiceAccount
  metadata:
    name: ingress-nginx-admission
  ```

Create it:
- `k apply -f nginx-ingress-definition.yml`


Ingress Example:
  ```
  apiVersion: networking.k8s.io/v1
  kind: Ingress
  metadata:
    name: my-ingress
  spec:
    rules:
    - host: mydomain.com
      http:
        paths:
        - path: /
          pathType: Prefix
          backend:
            service:
              name: backend1
              port:
                number: 80

        - host: mydomain2.com
          path: /
          pathType: Prefix
          backend:
            service:
              name: backend2
              port:
                number: 80  
  ```