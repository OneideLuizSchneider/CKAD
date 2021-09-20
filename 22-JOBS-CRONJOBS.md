How to create kubectl alias (optional):
- `alias k=kubectl`

Add a JOB:
  ```
  apiVersion: v1
  kind: Job
  metadata:
    name: math-job
  spec:
    completions: 1
    parallelism: 1
    backoffLimit: 4
    template:
      spec:
        containers:
        - name: math
          image: ubuntu
          command: ['expr','3','+','2']
        retartPolicy: Never
  ```

Get Jobs:
- `k get jobs`

Delete Jobs:
- `k delete job math`

Add a CronJob:
  ```
  apiVersion: v1
  kind: CronJob
  metadata:
    name: report-cronjob
  spec:
    schedule: "*/1 * * * *"
    jobTemplate:
      spec:
        completions: 1
        parallelism: 1
        template:
          spec:
            containers:
            - name: math
              image: ubuntu
              command: ['expr','3','+','2']
            retartPolicy: Never
  ```