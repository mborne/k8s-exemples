# Création d'un service whoami devant les Pods

## Pré-requis

* [whoami-deployment.md - Création de plusieurs Pod whoami à l'aide d'un Deployment](whoami-deployment.md)

## Principe

* Création du service "whoami" à l'aide de [whoami-service-lb.yaml](whoami-service-lb.yaml) avec `type: LoadBalancer`
* Récupération de l'IP externe du service (les IP des machines vagrantbox avec un déploiement K3S)
* Test d'accès au service

## Instruction

```bash
# Pré-requis - création du déploiement whoami
kubectl apply -f whoami-deployment.yaml
# Création du service "whoami" avec type: LoadBalancer
kubectl apply -f whoami-service-lb.yaml
# Affichage de la liste des services et contrôle colonne EXTERNAL-IP :
kubectl get svc
# Accès au service exposé sur vagrantbox-1 :
curl -sS http://192.168.50.201:8000
```

## Remarque

En alternative à l'utilisation d'un nouveau YAML, nous aurions pu procéder ainsi :

```bash
# pour modifier la définition avec "nano" plutôt que "vi"
export EDITOR=nano
# éditer le service pour modifier type=ClusterIP en LoadBalancer
kubectl edit svc/whoami
```

