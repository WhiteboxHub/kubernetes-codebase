# Frontend Deployment and Service Configuration

This document provides the configuration for the Kubernetes Deployment and Service for the WhiteBox Learning frontend application.

## Deployment Configuration

The deployment configuration is responsible for managing the lifecycle of the frontend application pods. It ensures that the specified number of replicas are running and handles updates and scaling.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend
  namespace: frontend
spec:
  replicas: 1
  selector:
    matchLabels:
        app: frontend
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
        - name: frontend
          image: whitebox-learning/frontend:latest
          ports:
            - containerPort: 3000
          envFrom:
            - secretRef:
                name: frontend-secrets
            - configMapRef:
                name: frontend-config
```

## Service Configuration

The service configuration is responsible for exposing the frontend application to the outside world.        It provides a stable IP address and port for the frontend application to use.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: frontend
  namespace: frontend
spec:
  selector:
    app: frontend
  ports:
    - protocol: TCP
      port: 3000
      targetPort: 3000
```


This configuration ensures that the frontend application is accessible from outside the Kubernetes cluster and can be scaled and managed as needed.

## Namespaces

The frontend application is deployed in the `frontend` namespace. This namespace isolates the frontend resources from other applications in the cluster.

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: frontend
```

This configuration ensures that the frontend application is deployed in the correct namespace and can be managed as needed.

## Ingress Configuration

The ingress configuration is responsible for routing traffic to the frontend application. It provides a stable URL for the frontend application to use.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: frontend
  namespace: frontend
```

This configuration ensures that the frontend application is accessible from outside the Kubernetes cluster and can be scaled and managed as needed.

## secrets and configMap


# Frontend Secrets Configuration

This document explains the configuration of the Kubernetes Secrets for the WhiteBox Learning frontend application.

## Overview

The secrets configuration is responsible for securely storing sensitive information such as API keys, passwords, and other confidential data. This ensures that sensitive information is not exposed in the application code or ConfigMaps.

## Secrets Example

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: frontend-secrets
type: Opaque
data:
  NEXTAUTH_URL: "https://www.whitebox-learning.com"
  GOOGLE_CLIENT_ID: "example.apps.googleusercontent.com"
  GOOGLE_CLIENT_SECRET: "example_secret"
  NEXTAUTH_SECRET: "your_secret_key"
  NEXT_PUBLIC_API_URL: "https://www.whitebox-learning.com/api/v1"
``` 

## Configuration Breakdown

### apiVersion and kind
- **apiVersion: v1**: Specifies the API version for the Secret resource.
- **kind: Secret**: Defines the type of Kubernetes object, which in this case is a Secret.

### Metadata
- **name: frontend-secrets**: The name of the Secret. This is used to identify the Secret within the Kubernetes cluster.

### Data
Holds the key-value pairs that make up the configuration data for the application.

- **NEXTAUTH_URL**: The URL for NextAuth, which is used for authentication.
- **GOOGLE_CLIENT_ID**: The Google Client ID for OAuth, used to authenticate users via Google.  
- **GOOGLE_CLIENT_SECRET**: The Google Client Secret for OAuth, used in conjunction with the Client ID for secure authentication.
- **NEXTAUTH_SECRET**: The secret key for NextAuth, used for signing and encryption.
- **NEXT_PUBLIC_API_URL**: The URL for the Next.js frontend application, used to access the API.

## ConfigMap

# Frontend Configuration

This document provides an example of a Kubernetes ConfigMap used for frontend configuration. Below is the ConfigMap definition followed by an explanation of each part.

## ConfigMap Example

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: frontend-config
data:
  NEXTAUTH_URL: "https://www.whitebox-learning.com"
  GOOGLE_CLIENT_ID: "example.apps.googleusercontent.com"
  GOOGLE_CLIENT_SECRET: "example_secret"
  NEXTAUTH_SECRET: "your_secret_key"
  NEXT_PUBLIC_API_URL: "https://www.whitebox-learning.com/api/v1"
```

## Configuration Breakdown

### apiVersion and kind
- **apiVersion: v1**: Specifies the API version for the ConfigMap resource.
- **kind: ConfigMap**: Defines the type of Kubernetes object, which in this case is a ConfigMap.

### Metadata
- **name: frontend-config**: The name of the ConfigMap. This is used to identify the ConfigMap within the Kubernetes cluster.

### Data
Holds the key-value pairs that make up the configuration data for the application.

- **NEXTAUTH_URL**: The URL for NextAuth, which is used for authentication.
- **GOOGLE_CLIENT_ID**: The Google Client ID for OAuth, used to authenticate users via Google.
- **GOOGLE_CLIENT_SECRET**: The Google Client Secret for OAuth, used in conjunction with the Client ID for secure authentication.
- **NEXTAUTH_SECRET**: The secret key for NextAuth, used for signing and encryption.
- **NEXT_PUBLIC_API_URL**: The URL for the Next.js frontend application, used to access the API.

This configuration ensures that the frontend application has the necessary information to authenticate users, securely access the API, and function correctly within the Kubernetes cluster.



