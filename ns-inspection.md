# Inspection des namespaces existants et de leur contenu

## Principe

* Lister les namespace existants
* Lister les Pods du namespace "kube-system"
* Lister les Pods dans tous les namespaces

## Instructions

```bash
# Lister les namespace existants 
kubectl get namespaces

# Lister les Pods du namespace "kube-system"
kubectl get pods -n kube-system

# Lister les Pods dans tous les namespaces
kubectl get pods -A
```

