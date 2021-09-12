In each container we can set its own env variables

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: postgres
  labels:
    tier: db-tier
spec:
  containers:
    - name: postgres
      image: postgres
      # env variables are set here
      env:
        - name: POSTGRES_PASSWORD
          value: mysecretpassword
```
