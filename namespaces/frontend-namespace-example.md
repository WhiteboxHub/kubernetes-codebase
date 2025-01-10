# Frontend Namespace Configuration

This document explains the configuration of the Kubernetes Namespace for the WhiteBox Learning frontend application.

## Overview

A Kubernetes Namespace is a way to divide cluster resources between multiple users. It is useful for creating multiple environments (e.g., development, staging, production) within the same cluster. The frontend namespace will isolate the resources used by the frontend application from other applications in the cluster.

## Namespace Example

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: frontend
```

## Configuration Breakdown

### apiVersion and kind
- **apiVersion: v1**: Specifies the API version of the Kubernetes Namespace resource. `v1` is the stable version for namespaces.
- **kind: Namespace**: Indicates that this configuration is for a Namespace resource, which is used to group resources within a cluster.

### Metadata
- **name: frontend**: The name of the namespace. This is used to identify the namespace within the Kubernetes cluster.


