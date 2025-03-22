#### Sidecar containers

- Here's an example of a Deployment with two containers, one of which is a sidecar:
  
  ```
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: myapp
    labels:
      app: myapp
  spec:
    replicas: 1
    selector:
      matchLabels:
        app: myapp
    template:
      metadata:
        labels:
          app: myapp
      spec:
        containers:
          - name: myapp
            image: alpine:latest
            command: ['sh', '-c', 'while true; do echo "logging" >> /opt/logs.txt; sleep 1; done']
            volumeMounts:
              - name: data
                mountPath: /opt
        initContainers:
          - name: logshipper
            image: alpine:latest
            restartPolicy: Always
            command: ['sh', '-c', 'tail -F /opt/logs.txt']
            volumeMounts:
              - name: data
                mountPath: /opt
        volumes:
          - name: data
            emptyDir: {}
  ```

- Two containers in a POD and sharing a volume, different mounthPaths but the same shared folder:

  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: two-containers
  spec:

    volumes:
    - name: shared-data
      emptyDir: {}

    containers:

    - name: nginx-container
      image: nginx
      volumeMounts:
      - name: shared-data
        mountPath: /usr/share/nginx/html

    - name: debian-container
      image: debian
      volumeMounts:
      - name: shared-data
        mountPath: /pod-data
      command: ["/bin/sh"]
      args: ["-c", "echo Hello from the debian container > /pod-data/index.html"]
  ```

---

Doc:
- <https://kubernetes.io/docs/concepts/workloads/pods/>