# Création d'un Pod avec une mauvaise de nginx

## Principe

* Création du Pod "nginx-ko" avec une version n'existant pas
* Suivre la création du Pod et constater `STATUS=ErrImagePull`
* Récupérer les informations détaillées
* Supprimer le Pod

## Instruction

```bash
# Création du Pod avec une version n'existant pas
kubectl run nginx-ko --image=nginx:7.4.1 --port=80 --restart=Always

# Suivre la création du Pod pour constater STATUS=ErrImagePull
kubectl get pods
# kubectl get pods -w

# Récupérer les informations détaillées
kubectl describe pod nginx-ko
kubectl get pod nginx-ko -o yaml

# Supprimer le Pod
kubectl delete pod nginx-ko
```



