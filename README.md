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

## Explorer l'API

> Objectif : écrire plus facilement et plus vite les YAML (utile pour les certifications)

Les commandes ci-après permettent de découvrir les types et paramètres disponibles au niveau de l'API :

```bash
# Lister les types d'objet
kubectl api-resources

# Voir la documentation d'un type d'objet
kubectl explain pod
# Voir les paramètres disponibles
kubectl explain pod.spec
kubectl explain pod.spec.containers
kubectl explain pod.spec.containers.envFrom --recursive
```

## Étendre l'API

> Objectif : comprendre l'extensibilité de l'API avec utilisation des schémas OpenAPI

```bash
# Lister les types d'objet ajoutés par cert-manager
kubectl api-resources --api-group=cert-manager.io
# Voir la définition du type ClusterIssuer de cert-manager
kubectl get crd clusterissuers.cert-manager.io -o yaml
```

## Aller plus loin

* [mborne/docker-devbox](https://github.com/mborne/docker-devbox) pour des exemples de déploiement plus réalistes avec helm
* [kubernetes.io - Concepts](https://kubernetes.io/docs/concepts/)
* [container.training - Deploying and Scaling Microservices with Docker and Kubernetes](https://container.training/kube-selfpaced.yml.html#1)
* [github.com - dgkanatsios/CKAD-exercises](https://github.com/dgkanatsios/CKAD-exercises/#ckad-exercises) pour des exercices corrigés préparant pour la certification CKAD et permettant de creuser certains aspects.

## Licence

[MIT](LICENSE)
