# Wordpress-Docker-Boilerplate
A simple boiler plate to set up Wordpress with Docker. The production mode includes traefik to automatically manage SSL.

## Dev set up
1. `cp ./.env.example .env` Create an envoiroment file using the example config 
1. `docker-compose up -d` to build and start the containers, network, and volumes. (remove the `-d` option if you want to see the cotainer's output)

## Production set up
A second `compose` file is provided to deploy a Wordpress instance for production. You could just run the standard `docker-compose.yml` file in production but `docker-compose.prod.yml` add Traefik to handle domain name routing and SSL encryption.
1. **MAKE SURE THAT PORTS 80, 443, AND 8080 ARE NOT BEING USED**
1. Create an envoiroment file using the example config `cp ./.env.example .env`
1. Make sure you've defined `SITEURL` and `AMCE_EMAIL` in your `.env` file. Traefik needs these to make SSL certifiates.
1. `docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d`