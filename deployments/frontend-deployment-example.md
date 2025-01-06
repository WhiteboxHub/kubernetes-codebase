# Frontend Deployment Configuration

This document explains the configuration of the Kubernetes Deployment for the WhiteBox Learning frontend application.

## Overview

The deployment configuration is responsible for managing the lifecycle of the frontend application pods. It ensures that the specified number of replicas are running and handles updates and scaling.


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
  template:
    metadata:
      labels:
        app: wbl-frontend-new
    spec:
      containers:
      - name: wbl-frontend-new
        image: remote123/whiteboxlearning:wbll-frontt5
        ports:
        - containerPort: 3000
        resources:
          requests:
            cpu: "200m"
            memory: "256Mi"
          limits:
            cpu: "500m"
            memory: "512Mi"
        envFrom:
        - configMapRef:
            name: frontend-config
```
## Configuration Breakdown

### apiVersion and kind
- **apiVersion: apps/v1**: Specifies the API version of the Kubernetes Deployment resource. `apps/v1` is the stable version for deployments.
- **kind: Deployment**: Indicates that this configuration is for a Deployment resource, which manages a set of identical pods.

### Metadata
- **name: wbl-frontend-new-deployment**: The name of the deployment. This is used to identify the deployment within the Kubernetes cluster.

### Spec
- **replicas: 1**: Specifies the desired number of pod replicas. In this case, only one instance of the application will be running.

#### Selector
- **matchLabels**: 
  - **app: wbl-frontend-new**: This label is used to identify the pods that belong to this deployment. It matches the labels defined in the pod template.

#### Template
- **metadata**:
  - **labels**: 
    - **app: wbl-frontend-new**: Labels applied to the pods created by this deployment. These labels are used for service discovery and management.

- **spec**:
  - **containers**: Defines the container specifications for the pods.
    - **name: wbl-frontend-new**: The name of the container.
    - **image: remote123/whiteboxlearning:wbll-frontt5**: The Docker image used for the container. This image contains the application code and dependencies.
    - **ports**:
      - **containerPort: 3000**: Exposes port 3000 on the container, which is the port the application listens on.
    - **resources**:
      - **requests**:
        - **cpu: "200m"**: The minimum amount of CPU resources requested for the container.
        - **memory: "256Mi"**: The minimum amount of memory requested for the container.
      - **limits**:
        - **cpu: "500m"**: The maximum amount of CPU resources the container can use.
        - **memory: "512Mi"**: The maximum amount of memory the container can use.
    - **envFrom**:
      - **configMapRef**:
        - **name: frontend-config**: References a ConfigMap named `frontend-config` to provide environment variables to the container. This allows for easy configuration management without hardcoding values in the deployment.

## Conclusion

This deployment configuration ensures that the frontend application is consistently running with the specified resources and environment settings. By using a ConfigMap for environment variables, it allows for flexible and secure configuration management. The deployment can be scaled by adjusting the `replicas` field, and resource requests and limits help manage application performance and stability.

