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


