# Frontend Service Configuration

This document explains the configuration of the Kubernetes Service for the WhiteBox Learning frontend application.

## Overview

The service configuration is responsible for exposing the frontend application to other services within the Kubernetes cluster. It provides a stable endpoint for accessing the application pods.


```yaml
apiVersion: v1
kind: Service
metadata:
  name: wbl-frontend-new-service
spec:
  type: ClusterIP
  selector:
    app: wbl-frontend-new
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
```
## Configuration Breakdown

### apiVersion and kind
- **apiVersion: v1**: Specifies the API version of the Kubernetes Service resource. `v1` is the stable version for services.
- **kind: Service**: Indicates that this configuration is for a Service resource, which provides network access to a set of pods.

### Metadata
- **name: wbl-frontend-new-service**: The name of the service. This is used to identify the service within the Kubernetes cluster.

### Spec
- **type: ClusterIP**: The type of service. `ClusterIP` is the default type and exposes the service on a cluster-internal IP. This means the service is only accessible within the cluster.
  
#### Selector
- **app: wbl-frontend-new**: This label selector is used to identify the pods that the service should route traffic to. It matches the labels defined in the deployment's pod template.

#### Ports
- **protocol: TCP**: The protocol used by the service. TCP is the default and most common protocol.
- **port: 80**: The port on which the service is exposed. This is the port that other services within the cluster will use to access the frontend application.
- **targetPort: 3000**: The port on the container to which the service should forward traffic. This should match the `containerPort` defined in the deployment configuration.

## Conclusion

This service configuration provides a stable internal endpoint for accessing the frontend application pods. By using a `ClusterIP` service, it ensures that the application is accessible within the cluster, allowing other services to communicate with it. The service routes traffic from port 80 to port 3000 on the application containers, facilitating seamless internal communication.