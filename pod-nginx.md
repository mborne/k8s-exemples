# Création d'un Pod avec un conteneur nginx

## Principe

* Créer un pod "nginx" utilisant l'image "nginx:1.14.2"
* Suivre la création du Pod (attente statut "Running")

## Instructions

```bash
# Création du Pod
kubectl run nginx --image=nginx:1.14.2 --port=80 --restart=Always

# Suivre la création du Pod (attendre "Running")
kubectl get pods
# kubectl get pods -w

# Accès sur http://localhost:8888
kubectl port-forward pod/nginx 8888:80

# Suivre (-f) les journaux applicatifs
kubectl logs pod/nginx -f

# Supprimer le Pod
kubectl delete pod nginx
```

## Alternative

Nous pourrions aussi créer le Pod avec la commande suivante exploitant le fichier [pod-nginx.yaml](pod-nginx.yaml) :

```bash
kubectl apply -f pod-nginx.yaml
```

## Remarques

* Le fichier [pod-nginx.yaml](pod-nginx.yaml) peut être généré à l'aide de la commande suivante :

```bash
kubectl --dry-run=client -o yaml run nginx --image=nginx:1.14.2 --port 80 > pod-nginx.yaml
```

* Cet ajout de `--dry-run=client -o yaml` permettra d'obtenir un premier jet pour de nombreux YAML
* Le plugin [kubectl-neat](https://github.com/itaysk/kubectl-neat#kubectl-neat) permettra de faire du ménage dans les déclarations inutiles :

```bash
kubectl run nginx --image=nginx:1.14.2 --port 80 --dry-run=client -o yaml | kubectl neat > pod-nginx.yaml
```

