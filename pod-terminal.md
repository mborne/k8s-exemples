# Création d'un Pod avec un conteneur nginx

## Principe

* Créer un Pod "terminal" avec l'image "ubuntu:22.04"
* Travailler dans le Pod
* Supprimer le Pod

## Instructions

```bash
# Créer un pod temporaire avec un terminal interactif
kubectl run terminal --rm -ti --image=ubuntu:22.04 --port=80 --restart=Never -- /bin/bash
# ... exécuter des commandes dans le Pod
apt-get update
apt-get install -y figlet
figlet hello!
# quitter le pod
exit
# constater sa suppression
kubectl get pods
```

## Alternative

```bash
# Créer un pod "terminal" temporaire
kubectl run terminal --image=ubuntu:22.04 --port=80 --restart=Never -- /bin/sleep 3600

# Suivre la création du Pod (attendre "Running")
kubectl get pods
# kubectl get pods -w

# Ouvrir un terminal dans le Pod
kubectl exec -ti terminal -- /bin/bash
# Exécuter des commandes dans le Pod...
apt-get update
apt-get install -y figlet
figlet hello!
# quitter le pod
exit
# Supprimer le Pod
kubectl delete pod terminal
```


