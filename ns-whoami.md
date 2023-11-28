# Déploiement de whoami dans un namespace dédié

## Principe

* Création du namespace "whoami"
* Création du déploiement "whoami" dans le namespace "whoami" avec [whoami-deployment.yaml](whoami-deployment.yaml)
* Création du service "whoami" dans le namespace "whoami" avec [whoami-service.yaml](whoami-service.yaml)
* Inspection du namespace

## Instructions

```bash
# Création du namespace whoami
kubectl create namespace whoami

# Création du déploiement dans le namespace
kubectl -n whoami apply -f whoami-deployment.yaml
# kubectl --namespace=whoami apply -f whoami-deployment.yaml

# Création du service dans le namespace
kubectl -n whoami apply -f whoami-service.yaml

# Inspection du namespace
kubectl -n whoami get all
```

## Remarque

* Sauf modification de configuration, nous travaillons dans le namespace "default" en l'absence de `--namespace`
* Vous n'aurez pas forcément la main sur la création des namespaces (**Namespace as a service**)