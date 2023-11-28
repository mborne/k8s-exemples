# k8s-exemples

Quelques exemples pour la découverte de Kubernetes...

## Prise en main

> Objectif : prise en main kubectl, découverte Pod, debug...

* [pod-terminal.md - Création d'un Pod avec un conteneur ubuntu](pod-terminal.md)
* [pod-nginx.md - Création d'un Pod avec un conteneur nginx](pod-nginx.md)
* [pod-nginx-ko.md - Création d'un Pod avec une mauvaise de nginx](pod-nginx-ko.md)

## Deployment et Service

* [whoami-deployment.md - Création de plusieurs Pod whoami à l'aide d'un Deployment](whoami-deployment.md)
* [whoami-service.md - Création d'un service whoami devant ces Pods](whoami-service.md)

## Namespaces

> Objectifs : Travail dans un namespace, découverte du namespace "kube-system",...

* [ns-inspection.md - Inspection des namespaces existants et de leur contenu](ns-inspection.md)
* [ns-whoami.md - Déploiement de whoami dans un namespace dédié](ns-whoami.md)

## Ingress

> Objectifs : Ingress et Ingress Controller

* [traefik.md - Installation de Traefik en tant qu'Ingress Controller](traefik.md)
* [whoami-ingress.md - Exposition du service whoami sur une URL avec une ressource Ingress](whoami-ingress.md)

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
