
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

### Explanation

- `apiVersion: apps/v1`: Specifies the API version of the Kubernetes object. `apps/v1` is the stable version for deployments.
- `kind: Deployment`: Indicates that this configuration is for a Deployment, which manages a set of identical pods.
- `metadata`: Contains data that helps uniquely identify the object, including a `name`.
  - `name: frontend-deployment`: The name of the deployment. You can use this name with `kubectl` commands, e.g., `kubectl get deployment frontend-deployment`.
- `spec`: Defines the desired state of the deployment.
  - `replicas: 3`: Specifies the number of pod replicas to run. You can scale this with `kubectl scale deployment frontend-deployment --replicas=5`.
  - `selector`: Defines how the deployment finds which pods to manage.
    - `matchLabels`: A set of key-value pairs used to select pods.
      - `app: frontend`: The label used to identify the pods managed by this deployment.

The following YAML configuration defines a deployment for the `wbl-frontend-new` application.
