## Running Gateway API Echo Basic

### Docker Run Example

```bash
docker run --rm -p 3000:3000 dhi.io/gateway-api:1.5.1
```

Then test:

```bash
curl http://localhost:3000/test
```

### Kubernetes Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: echo-basic
spec:
  replicas: 1
  selector:
    matchLabels:
      app: echo-basic
  template:
    metadata:
      labels:
        app: echo-basic
    spec:
      containers:
        - name: echo-basic
          image: dhi.io/gateway-api:1.5.1
          ports:
            - containerPort: 3000
          securityContext:
            runAsNonRoot: true
            runAsUser: 65532
```

For more details, visit the upstream documentation:
https://gateway-api.sigs.k8s.io/
