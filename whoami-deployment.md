# Création de plusieurs Pod whoami à l'aide d'un Deployment

## Principe

* Création du déploiement à l'aide de [whoami-deployment.yaml](whoami-deployment.yaml)
* Inspection du déploiement
* Inspection des Pods du déploiement (attente statut "Running")
* Passage de 3 à 5 Pods
* Nouvelle inspection du déploiement

## Instructions

```bash
# Création du déploiement
kubectl apply -f whoami-deployment.yaml

# Inspection du déploiement
kubectl get deploy whoami -o wide

# Inspection des Pods du déploiement
# (filtrage par label app=whoami)
kubectl get pods -l app=whoami
# Alternative : lancer la commande suivante dans une fenêtre séparée
# kubectl get pods -l app=whoami -w

# Passer de 3 à 5 pods
kubectl scale deploy/whoami --replicas=5

# Nouvelle inspection du déploiement
kubectl get deploy whoami -o wide
```

## Génération du YAML

[whoami-deployment.yaml](whoami-deployment.yaml) est obtenu à l'aide de la commande suivante :

```yaml
kubectl --dry-run=client -o yaml create deploy whoami --image=traefik/whoami:v1.10.2 --replicas=3 > whoami-deployment.yaml
```

## Aller plus loin

En coulisse des déploiements, Kubernetes manipule des ReplicaSet non détaillés dans ce cours. Vous pourrez tester les commandes suivantes :

```bash


# Mettre à jour l'image
kubectl set image deploy/whoami whoami=traefik/whoami:v1.9.0
kubectl get deploy whoami -o wide

# Lister les replicasets
kubectl get replicaset -o wide

# Annuler la mise à jour de l'image
kubectl rollout undo deploy/whoami
kubectl get deploy whoami -o wide
```



