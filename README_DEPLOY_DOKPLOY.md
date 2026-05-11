# Déploiement OpenAlgo sur Dokploy

## Stratégie

Ce fork contient un fichier `docker-compose.dokploy.yml` adapté à Dokploy.

Les ports ne sont pas publiés directement sur l'hôte. On utilise `expose`, puis Dokploy/Traefik route le trafic via le domaine configuré dans l'interface.

## Service principal

Service : openalgo  
Port HTTP : 5000  
Port WebSocket : 8765  

## Volumes persistants

- openalgo_db → /app/db
- openalgo_log → /app/log
- openalgo_strategies → /app/strategies
- openalgo_keys → /app/keys
- openalgo_tmp → /app/tmp

## Configuration Dokploy

Créer un Compose Service dans Dokploy.

Repository :
https://github.com/Jeffreyapi/openalgo

Branch :
dokploy-production

Compose file :
docker-compose.dokploy.yml

Domain :
openalgo.example.com

Service :
openalgo

Container port :
5000

## Mise à jour depuis upstream

```bash
git checkout main
git fetch upstream
git merge upstream/main
git push origin main

git checkout dokploy-production
git merge main
git push origin dokploy-production