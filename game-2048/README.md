# game-2048

Déploiement de [twoseven1408/game-2048:latest](https://hub.docker.com/layers/twoseven1408/game-2048/latest/images/sha256-338a89c44a060734afb446950fbbcd804a005daf7af38def7c496967fa4ab965) à l'aide de Kuztomize.

## Principe

* [game-2048/manifest/base](https://github.com/mborne/k8s-exemples/blob/master/game-2048/manifest/base) définit un *Deployment* et un *Service*
* [game-2048/manifest/devbox](https://github.com/mborne/k8s-exemples/blob/master/game-2048/manifest/devbox) ajoute un *Ingress* en https://game-2048.dev.localhost avec *traefik* et un certificat autosigné.



