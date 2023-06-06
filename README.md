# k8s-exemples

Quelques exemples pour la découverte de Kubernetes...

## Prise en main

* [Création d'un Pod avec un conteneur nginx pour découverte kubectl](pod-nginx.md)

## Deployment et Service

* [whoami/deployment.yaml](whoami/deployment.yaml) - Création de plusieurs Pod whoami à l'aide d'un Deployment

```bash
kubectl apply -f whoami/deployment.yaml
kubectl get pods
```

* [whoami/service.yaml](whoami/service.yaml) - Création d'un service whoami devant ces Pods

```bash
kubectl apply -f whoami/service.yaml
# Pour http://localhost:8888
kubectl port-forward svc/whoami 8888:80
```

## Namespaces

* Inspection des namespaces existants et de leur contenu :

```bash
kubectl get namespaces
kubectl -n kube-system get pods,svc
```

* Création d'un namespace et déploiement dans un namespace :

```bash
kubectl create namespace whoami
kubectl -n whoami apply -f whoami/deployment.yaml
kubectl -n whoami apply -f whoami/service.yaml
kubectl -n whoami get all
```

