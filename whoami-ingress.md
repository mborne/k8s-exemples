# Exposition du service whoami sur une URL avec une ressource Ingress

## Pré-requis

* [traefik.md - Installation de Traefik en tant qu'Ingress Controller](traefik.md)
* [ns-whoami.md - Déploiement de whoami dans un namespace dédié](ns-whoami.md)

## Principe

* Vérifier la résolution de nom de `whoami.dev.quadtreeworld.net` sur [vagrantbox-1](https://github.com/mborne/vagrantbox#vagrantbox)
* Créer la ressource [whoami-ingress.yaml](whoami-ingress.yaml)
* Tester l'accès au service via une URL et constater la répartition de charge

## Instructions

```bash
# Vérifier la résolution de nom
host whoami.dev.quadtreeworld.net
#whoami.dev.quadtreeworld.net is an alias for lb-dev.quadtreeworld.net.
#lb-dev.quadtreeworld.net has address 192.168.50.201

# Déployer la ressource Ingress et consulter http://whoami.dev.quadtreeworld.net
kubectl -n whoami apply -f whoami-ingress.yaml
```
