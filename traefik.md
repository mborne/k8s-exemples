# Installation de Traefik en tant qu'Ingress Controller

## Principe

Nous nous appuyons sur un chart Helm existant (https://helm.traefik.io/traefik) pour installer [Traefik](https://doc.traefik.io/traefik/) en tant que **Ingress Controller**.

## Instructions

### Installation

```bash
# Ajouter le chart helm
helm repo add traefik https://helm.traefik.io/traefik

# Mettre à jour les dépôts helm
helm repo update

# Créer le namespace "traefik-system" s'il n'existe pas
# (nous pourrions aussi ajouter --create-namespace à la commande suivante)
kubectl create namespace traefik-system --dry-run=client -o yaml | kubectl apply -f -

# Déployer traefik dans le namespace "traefik-system"
# (avec activation du dashboard au niveau du service)
helm -n traefik-system upgrade --install traefik traefik/traefik -f traefik/values.yaml
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

