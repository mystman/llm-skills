# Example: manifest review request

## Sample input

Review this Deployment and Service. The Service has no endpoints.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: payments-api
  namespace: demo
spec:
  replicas: 2
  selector:
    matchLabels:
      app: payments-api
  template:
    metadata:
      labels:
        app: payment-api
    spec:
      containers:
        - name: api
          image: ghcr.io/example/payments:1.4.2
          ports:
            - containerPort: 8000
---
apiVersion: v1
kind: Service
metadata:
  name: payments-api
  namespace: demo
spec:
  selector:
    app: payments-api
  ports:
    - port: 80
      targetPort: 8080
```

## Expected behavior

- identify the Deployment label mismatch
- identify the Service `targetPort` mismatch
- return corrected YAML
- explain why the Service had no endpoints
- suggest safe validation commands
