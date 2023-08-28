# odoo

### Installing Odoo 16.0 with one command (Supports multiple Odoo instances on one server).


## Prérequis

- Install docker and docker-compose yourself
- Docker Compose installé sur la machine hôte

## Utilisation

1. Assurez-vous que Docker et Docker Compose sont installés sur votre système.

2. Start the container:

docker-compose up

Cela lancera les conteneurs Odoo et PostgreSQL en arrière-plan.

Vous pouvez accéder à l'interface Odoo en ouvrant un navigateur web et en visitant http://localhost:80.

3. Pour arrêter les conteneurs, exécutez : 
 
  docker-compose down

  # Configuration

Ce fichier `docker-compose.yml` définit la configuration des services Docker utilisés pour exécuter Odoo et PostgreSQL dans un environnement conteneurisé.

## Service "web" (Odoo)

- Image utilisée : `odoo:16.0`
- Ports exposés : `80:8069` (interface Odoo accessible depuis le port 80 du navigateur)
- Dépendances : le service "db" (PostgreSQL)
- Volumes montés :
  - `odoo-web-data` : données persistantes pour Odoo
  - `./config` : fichiers de configuration d'Odoo
  - `./addons` : addons personnalisés pour Odoo
- Réseau : `odoo_network`

## Service "db" (PostgreSQL)

- Image utilisée : `postgres:15`
- Variables d'environnement :
  - `POSTGRES_DB` : base de données PostgreSQL
  - `POSTGRES_PASSWORD` : mot de passe de la base de données
  - `POSTGRES_USER` : utilisateur PostgreSQL
  - `PGDATA` : emplacement des données PostgreSQL
- Volumes montés : `odoo-db-data` (données persistantes pour PostgreSQL)
- Réseau : `odoo_network`

## Volumes et Réseau

Ce projet utilise des volumes Docker pour stocker les données de manière persistante, ainsi qu'un réseau personnalisé pour connecter les conteneurs.

### Volumes :

- `odoo-web-data` : données persistantes pour Odoo
- `odoo-db-data` : données persistantes pour PostgreSQL

### Réseau :

- `odoo_network` : réseau personnalisé pour connecter les conteneurs Odoo et PostgreSQL

![good luck](odoo/photo/odoo-16-welcome-screenshot.png)

