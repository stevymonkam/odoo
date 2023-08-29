
#odoo

### Installing Odoo 16.0 with one command (Supports multiple Odoo instances on one server).


## Prerequisites

- Install docker and docker-compose yourself
- Docker Compose installed on the host machine

## Use

1. Make sure Docker and Docker Compose are installed on your system.

2. Start the container:

```bash
   docker-compose-up
```
This will launch Odoo and PostgreSQL containers in the background.

You can access the Odoo interface by opening a web browser and visiting http://localhost:80.

3. To stop the containers, run:
 
 
```bash
  docker-compose down
```

  # Setup

This `docker-compose.yml` file defines the configuration of Docker services used to run Odoo and PostgreSQL in a containerized environment.

## "Web" service (Odoo)

- Image used: `odoo:16.0`
- Exposed ports: `80:8069` (Odoo interface accessible from browser port 80)
- Dependencies: the "db" service (PostgreSQL)
- Mounted volumes:
  - `odoo-web-data`: persistent data for Odoo
  - `./config`: Odoo configuration files
  - `./addons`: custom addons for Odoo
- Network: `odoo_network`

## Service "db" (PostgreSQL)

- Image used: `postgres:15`
- Environment variables:
  - `POSTGRES_DB`: PostgreSQL database
  - `POSTGRES_PASSWORD`: database password
  - `POSTGRES_USER`: PostgreSQL user
  - `PGDATA`: PostgreSQL data location
- Mounted volumes: `odoo-db-data` (persistent data for PostgreSQL)
- Network: `odoo_network`

## Volumes and Network

This project uses Docker volumes to store data persistently, along with a custom network to connect the containers.

### Volumes:

- `odoo-web-data`: persistent data for Odoo
- `odoo-db-data`: persistent data for PostgreSQL

### Network :

- `odoo_network`: custom network to connect Odoo and PostgreSQL containers


## docker-compose.yml

* odoo:16.0
* postgres:15

## Odoo 16.0 screenshots after successful installation.

<img src="photo/odoo-16-welcome-screenshot.png" width="50%">

<img src="photo/odoo-16-apps-screenshot.png" width="100%">

<img src="photo/odoo-16-sales-screen.png" width="100%">

<img src="photo/odoo-16-product-form.png" width="100%">


