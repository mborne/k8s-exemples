# Lister les types définis au niveau de l'API Kubernetes

## Principe

* Lister tous les types d'objets définis au niveau de l'API
* Filtrer par "api-group"

## Instructions

```bash
# Lister tous les types d'objet
kubectl api-resources

# Filtrer sur les types de base (Pod, Namespace, ConfigMap, Secret,...)
kubectl api-resources --api-group=''
# Les charges de travail (Deployment, StatefulSet, DaemonSet, ReplicaSet...)
kubectl api-resources --api-group='apps'
# RBAC - La gestion des droits (Role/RoleBinding, ClusterRole/ClusterRoleBinding...)
kubectl api-resources --api-group 'rbac.authorization.k8s.io'
# Les concepts pour le stockage (StorageClass, VolumeAttachment, CSIDriver, ...)
kubectl api-resources --api-group='storage.k8s.io'
```
