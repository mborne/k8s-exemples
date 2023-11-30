# Installer cert-manager et explorer les types définis (CRD)

## Principe

* [Installer cert-manager avec Helm](https://cert-manager.io/docs/installation/helm/#steps)
* Lister les types d'objet ajoutés par cert-manager
* Voir la définition du type ClusterIssuer de cert-manager

## Instructions

```bash
#-------------------------------------------------
# Installation de cert-manager avec helm
#-------------------------------------------------

# Ajout du dépôt
helm repo add jetstack https://charts.jetstack.io
# Mise à jour des dépôts
helm repo update
# Installation dans un namespace cert-manager
helm upgrade --install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.13.2 \
  --set installCRDs=true

#-------------------------------------------------
# Inspection des CRD
#-------------------------------------------------

# Lister les types d'objet ajoutés par cert-manager
kubectl api-resources --api-group=cert-manager.io
# Voir la définition du type ClusterIssuer de cert-manager
# (en particulier schema.openAPIV3Schema)
kubectl get crd clusterissuers.cert-manager.io -o yaml | more
```

## Remarques

Les développeurs web reconnaîtront normalement un format bien connus pour la spécification des API. Pour les autres :

* [apicarto.ign.fr - codes-postaux](https://apicarto.ign.fr/api/doc/codes-postaux#/) / [codes-postaux.yml](https://apicarto.ign.fr/api/doc/codes-postaux.yml) donnera un exemple trivial d'API spécifiée selon ce principe.
* [editor.swagger.io](https://editor.swagger.io/) donnera un exemple ("Swagger Petstore - OpenAPI 3.0", les spécifications d'une API de gestion d'une boutique d'animaux) plus complet.



