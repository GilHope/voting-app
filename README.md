# Voting-App

## Overview

A simple, interactive practice demo project which showcases a multi-tier application in a containerized environment. 

### voting-app-pod
(accessed by users)
- port 80

### redis-pod 
(accessed by worker-pod and voting-app-pod)
- the voting-app saves the vote to redis database
- worker-app reads the vote from the redis db
- port 6379

### worker-app-pod
- reads count of votes from redis db and then updates that count to postgres db

### posgres-pod
(accessed by worker-pod and result-app-pod)
- worker-app updates with the total vote count
- result-app reads from it to display that vote count in browser
- port 5432

### result-app-pod
(accessed by users)
- port80

# How To Create A Configuration File In YAML

## Required Fields
- apiVersion
- kind
- metadata
- spec

### apiVersion

The 'apiVersion' field in a YAML file specifies the version of the K8s API that the resource will adhere to and ensures the compatibility between the YAML file and the K8s cluster.

- The 'v1' apiVersion was the first table release of the Kubernetes API and contains many of the core objects.

- The 'apps/v1' apiVersion is the most common API group in K8s and includes the functionality related to running applications on K8s, like deplyoments, rolling updates, adn replica sets.

### Kind

The 'kind' field defines the type of resource beting created and informs K8s how to interpret and manage the resource.

### metadata

The 'metadata' field contians important information regarding the resource and works to identify and organize resources within the desired cluster. 

### spec

The 'spec' field describes the desired state of the resource and outlines the configuration details and the behavior of the resource.

## Kind / apiVersion Relationship

### Core Group (v1 group)
- POD - v1
- Service - v1
- Namespace - v1
- ConfigMap - v1
- Secret - v1
- PersistentVolume - v1
- PersistentVolumeClaim - v1

### Apps Group
- ReplicaSet - apps/v1
- Deployment - apps/v1
- StatefulSet - apps/v1
- DaemonSet - apps/v1

### Batch Group
- Job - batch/v1
- CronJob - batch/v1 or batch/v1beta1

### Networking Group
- Ingress - networking.k8s.io/v1
- NetworkPolicy - networking.k8s.io/v1

### RBAC Authorization Group
- Role - rbac.authorization.k8s.io/v1
- ClusterRole - rbac.authorization.k8s.io/v1
- RoleBinding - rbac.authorization.k8s.io/v1
- ClusterRoleBinding - rbac.authorization.k8s.io/v1