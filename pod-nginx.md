# Création d'un Pod avec un conteneur nginx pour découverte kubectl

## Principe

* Créer un Pod "nginx" avec l'image "nginx:1.14.2"
* Suivre la création du Pod
* Récupérer des information sur le Pod
* Accéder à un port du Pod
* Récupérer les logs du Pod
* Supprimer le Pod

## Instructions

Les commandes ci-après permettront de créer le Pod et de surveiller son démarrage :

```bash
# Création du Pod
kubectl run nginx --image=nginx:1.14.2 --port 80
# Récupération de la liste des Pods
kubectl get pods
# Idem avec watch pour attendre "Running"
kubectl get pods -w
```

Les commandes ci-après seront utiles pour récupérer des informations sur le Pod (elles seront utiles pour diagnostiquer des problèmes de démarrage) :

```bash
# Description du Pod
kubectl describe pod nginx
# Récupération des détails du Pod
kubectl get pod nginx -o yaml
```

Nous pourrons accéder au port 80 sur Pod en exploitant la fonctionnalité port-forward :

```bash
# Accès sur http://localhost:8888
kubectl port-forward pod/nginx 8888:80
```

Nous pourrons accéder aux logs comme suit :

```bash
kubectl logs pod/nginx -f
```

Enfin, nous pourrons supprimer le Pod comme suit :

```bash
kubectl delete pod nginx
```

## Remarques

* Vous pourrez tenter la création d'un Pod avec une version n'existant pas : `kubectl run nginx-ko --image=nginx:7.4.1 --port 80`

* Nous pourrions aussi créer le Pod avec la commande suivante exploitant le fichier [pod-nginx.yaml](pod-nginx.yaml) :

```bash
kubectl apply -f pod-nginx.yaml
```

* L'utilisation de `--dry-run=client -o yaml` combinée à l'utilisation du plugin [kubectl-neat](https://github.com/itaysk/kubectl-neat#kubectl-neat) pour kubectl nous aidera à obtenir un premier jet pour les fichiers YAML :

```bash
kubectl run nginx --image=nginx:1.14.2 --port 80 --dry-run=client -o yaml | kubectl neat
```

