# Explorer les spécifications des objets définis dans l'API Kubernetes

## Principe

* Voir la documentation du type Pod
* Creuser dans les spécifications des paramètres
* Pouvoir mémoriser uniquement `pod.spec.volumes`, `pod.spec.containers.envFrom`...

## Instructions

### Pour comprendre le principe...

```bash
# Voir la documentation d'un type d'objet
kubectl explain pod

# Pour découvrir l'ensemble des possibles...
kubectl explain pod.spec
```

### Pour le placement...

```bash
# Pour placer un Pod sur un noeud précis...
kubectl explain pod.spec.nodeName
# Pour placer un Pod par label...
kubectl explain pod.spec.nodeSelector

# Pour des règles de placement plus complexes...
kubectl explain pod.spec.affinity.nodeAffinity --recursive
```

### Pour la configuration...

```bash
# Pour le passage des variables d'environnement
kubectl explain pod.spec.containers
kubectl explain pod.spec.containers.envFrom --recursive
```

### Pour le stockage...

```bash
# Pour un volume emptyDir (ex : cache applicatif)
kubectl explain pod.spec.volumes.emptyDir
# Pour un volume hostPath (DEBUG, collecte des logs,...)
kubectl explain pod.spec.volumes.hostPath

# Pour monter les ConfigMap (ex : fichier de conf.)
kubectl explain pod.spec.volumes.configMap
# Pour monter les Secret (ex : certificats)
kubectl explain pod.spec.volumes.secret
```



