# Frontend Deployment Example

This is an example of a Kubernetes deployment configuration for the frontend service.

## Deployment Configuration

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: frontend
``` 


The following YAML configuration defines a deployment for the `wbl-frontend-new` application.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wbl-frontend-new-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: wbl-frontend-new
```

        