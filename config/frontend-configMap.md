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
