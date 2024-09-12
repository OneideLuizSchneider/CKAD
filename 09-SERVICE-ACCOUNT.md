## Service Account

- Get all service accounts:
  ```
  k get sa -A
  ```

- Service Account for the POD:
  ```
  k create serviceaccount my-sa
  ```
- To get the name of the token to see the value of the token:
  ```
  k describe serviceaccount my-sa
  k describe secret my-sa-token-kbbdm
  ```

Default Service Account is mounted on `/var/run/secrets`
