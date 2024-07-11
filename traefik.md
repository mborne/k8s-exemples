# Installation de Traefik en tant qu'Ingress Controller

Pour que les ressources **Ingress** soit interprétées, il convient de s'assurer qu'un **Ingress Controller** est installé dans le cluster Kubernetes.

## Cas de K3S

**Avec K3S, l'installation de Traefik est traitée par défaut**. Nous pourrons nous contenter de vérifier :

```bash
# vérification de la présence de l'ingressclass
kubectl get ingressclass
#NAME      CONTROLLER                      PARAMETERS   AGE
#traefik   traefik.io/ingress-controller   <none>       12m

# Vérification de la présence du service traefik de type loadbalancer avec 
# EXTERNAL-IP contenant les IP des VM vagrantbox
kubectl -n kube-system get svc traefik
# NAME      TYPE           CLUSTER-IP      EXTERNAL-IP         PORT(S)                      AGE
#traefik   LoadBalancer   10.43.118.132   192.168.50.201,...   80:30614/TCP,443:32086/TCP   25m
```

## Installation avec Helm

Si tel n'était pas le cas, nous pourrions utiliser [Helm](https://mborne.github.io/cours-devops/annexe/kubernetes/helm.html) pour installer [Traefik](https://doc.traefik.io/traefik/) à l'aide d'un chart existant : https://helm.traefik.io/traefik

### Installation

```bash
# Ajouter le chart helm
helm repo add traefik https://helm.traefik.io/traefik

# Mettre à jour les dépôts helm
helm repo update

# Déployer traefik dans le namespace "traefik-system"
helm -n traefik-system  upgrade --install --create-namespace traefik traefik/traefik
```

### Contrôle de l'installation

```bash
# Inspecter les ressources
kubectl -n traefik-system get pod,svc

# Contrôler la création de la classe ingress
kubectl get ingressclass
```

### Accès au dashboard 

```bash
# Pour avoir accès au dashboard sur http://127.0.0.1:9000/dashboard/ :
kubectl -n traefik-system port-forward svc/traefik 9000:9000
```

## Remarques

* L'ensemble des paramètres disponibles peut être obtenu à l'aide de la commande `helm show values traefik/traefik`
* Voir [mborne/docker-devbox - cert-manager](https://github.com/mborne/docker-devbox/tree/master/cert-manager#cert-manager) et [mborne/docker-devbox - traefik](https://github.com/mborne/docker-devbox/tree/master/traefik#traefik) pour une installation plus complète.
* Voir [mborne/docker-devbox - nginx-ingress-controller](https://github.com/mborne/docker-devbox/tree/master/nginx-ingress-controller#nginx-ingress-controller) pour une alternative à Traefik.

