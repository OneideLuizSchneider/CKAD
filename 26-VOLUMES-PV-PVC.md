#### Persistent Volumes and PV. Claims

Persistent Volumes:
  ```
  apiVersion: v1
  kind: PersistentVolume
  metadata:
    name: pv-log
  spec:
    capacity:
      storage: 100Mi
    accessModes:
    - ReadWriteMany
    persistentVolumeReclaimPolicy: Retain
    hostPath:
      path: /pv/log
  ```

Create it:
- `k apply -f pv-definition.yml`


PVC:
  ```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  capacity:
    storage: 1Gi
  resources:
    requests:
      storage: 500Mi
  accessModes:
    - ReadWriteOnce
  ```  

POD:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: mypod
  spec:
    containers:
      - name: my-nginx
        image: nginx
        volumeMounts:
        - mountPath: "/var/www/html"
          name: mypd
    volumes:
      - name: mypd
        persistentVolumeClaim:
          claimName: my-pvc
  ```

---

Doc:
- <https://kubernetes.io/docs/concepts/storage/volumes/>
- <https://kubernetes.io/docs/concepts/storage/persistent-volumes/>