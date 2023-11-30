# k8s-exemples

Quelques **exemples pour la découverte des concepts de Kubernetes** dans le cadre de [mborne.github.io - cours-devops - DevOps avec Kubernetes](https://mborne.github.io/cours-devops#2).

## Pod

> Objectif : prise en main kubectl, découverte Pod, debug...

* [pod-terminal.md - Création d'un Pod avec un conteneur ubuntu](pod-terminal.md)
* [pod-nginx.md - Création d'un Pod avec un conteneur nginx](pod-nginx.md)
* [pod-nginx-ko.md - Création d'un Pod avec une mauvaise de nginx](pod-nginx-ko.md)

## Deployment

> Objectif : création de plusieurs Pods à partir d'un modèle (template)

* [whoami-deployment.md - Création de plusieurs Pod whoami à l'aide d'un Deployment](whoami-deployment.md)

## Service

> Objectif : créer un service ClusterIP, accéder au service,...

* [whoami-service.md - Création d'un service whoami devant ces Pods](whoami-service.md)

## Ingress

> Objectifs : Créer une ressource Ingress (noter la variabilité selon les environnements), déployer Ingress Controller pour tester...

* [traefik.md - Installation de Traefik en tant qu'Ingress Controller](traefik.md)
* [whoami-ingress.md - Exposition du service whoami sur une URL avec une ressource Ingress](whoami-ingress.md)

## Namespace

> Objectifs : Travail dans un namespace, découverte du namespace "kube-system",...

* [ns-inspection.md - Inspection des namespaces existants et de leur contenu](ns-inspection.md)
* [ns-whoami.md - Déploiement de whoami dans un namespace dédié](ns-whoami.md)

## API

> Objectif : Niveau 2, comprendre l'API, explorer les spécifications pour découvrir les options possibles et écrire plus facilement les YAML, comprendre l'extensibilité de l'API avec utilisation des schémas OpenAPI (CRD),...

* [api-resources.md - Lister les types définis au niveau de l'API](api-resources.md)
* [explain.md - Explorer les spécifications des objets définis dans l'API Kubernetes](explain.md)
* [crd-cert-manager.md - Installer cert-manager et explorer les types définis (CRD)](crd-cert-manager.md)

## Aller plus loin

* [mborne/docker-devbox](https://github.com/mborne/docker-devbox) pour des exemples de déploiement plus réalistes avec [Helm](https://helm.sh/).
* [kubernetes.io - Concepts](https://kubernetes.io/docs/concepts/)
* [container.training - Deploying and Scaling Microservices with Docker and Kubernetes](https://container.training/kube-selfpaced.yml.html#1)
* [github.com - dgkanatsios/CKAD-exercises](https://github.com/dgkanatsios/CKAD-exercises/#ckad-exercises) pour des exercices corrigés préparant pour la certification CKAD et permettant de creuser certains aspects.

## Licence

[MIT](LICENSE)
