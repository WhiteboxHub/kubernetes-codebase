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
```
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

## Purpose

This ConfigMap provides configuration data to the frontend application running in the Kubernetes cluster. By using a ConfigMap, you can manage configuration settings separately from the application code, allowing for easier updates and management. This approach also helps in maintaining consistency across different environments (e.g., development, staging, production) by simply changing the ConfigMap values.
## Security Note

While ConfigMaps are great for managing configuration data, they are not intended for storing sensitive information like passwords or API keys. For sensitive data, consider using Kubernetes Secrets, which provide a more secure way to handle confidential information.

## Conclusion

The `frontend-config` ConfigMap is a crucial part of the application's configuration management, ensuring that the necessary environment variables are available to the application without hardcoding them into the application code.