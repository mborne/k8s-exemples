# Exposition du service whoami sur une URL avec une ressource Ingress

## Pré-requis

* [traefik.md - Installation de Traefik en tant qu'Ingress Controller](traefik.md)
* [ns-whoami.md - Déploiement de whoami dans un namespace dédié](ns-whoami.md)

## Principe

* Constater que `*.dev.quadtreeworld.net` est configuré pour résoudre sur l'IP de vagrantbox-1
* Créer la ressource [whoami-ingress.yaml](whoami-ingress.yaml) s'appuyant sur ce point
* Tester l'accès à l'URL

```bash
# Constater que *.dev.quadtreeworld.net est configuré pour résoudre sur l'IP de vagrantbox-1
host whoami.dev.quadtreeworld.net

# Déployer la ressource Ingress et consulter http://whoami.dev.quadtreeworld.net
kubectl -n whoami apply -f whoami-ingress.yaml
```
