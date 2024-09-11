## Helm

#### Install

Go to <https://helm.sh/docs/intro/install/>

#### Some commands

- `helm search hub` searches the Artifact Hub, which lists helm charts from dozens of different repositories.
- `helm search repo` searches the repositories that you have added to your local helm
  ```
  helm search repo wordpress
  helm search hub wordpress
  ```

- Add a Repo:
  ```
  helm repo add bitname https://charts.bitnami.com/bitnami
  helm repo update
  ```

- Search for a repo:
  `helm search repo joomla`

- List repositories:
  `helm repo ls`

- Env prints out all the environment info in use by Helm
  `helm env`

- Install App:
  - `helm install <name> <chart>`
  - Ex.: `helm install my-nginx stable/nginx-ingress`
- Uninstall App:
  - `helm uninstall <name>`
  - Ex.: `helm uninstall my-nginx`
- You can pass `--namespace my-namespace` as well

- Pull and download:
  - `helm pull <chart> --untar=true`

Some Cheats:
<https://helm.sh/docs/intro/cheatsheet/>