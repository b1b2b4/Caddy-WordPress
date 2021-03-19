# Caddy-Wordpress
Deploy WordPress Behind Caddy 2.3.0 using Docker Compose

## Contents of the Repository
This repository contains WordPress application running behind Caddy, supported by Docker and orchestrated by Docker Compose.

It Includes:

A container for Caddy;\
A container for WordPress;\
A container for MariaDB;\
A container for Adminer;

## Pre-Requisites
Make sure Docker and Docker Compose installed on the server where you are going to install the stack.

make sure you created caddyconfig, caddydata and caddylogs folders in the drirectory where you have docker-compose file. ***Caddy's data directory is most important one, don't forget to persist it. If you forgot to persist, you will hit rate limit for getting Letsencrypt certificates.***

Also create wordpress and db folders as well in the same directory to persist WordPress and MariaDB data.

## Install or Set up WordPress
Clone or Download this repository. Once after getting the repository, run ```docker-compose up -d``` and wait for the containers to configure the WordPress site.

Open the domain, example.com in the web browser. Create an admin account and click the Install WordPress button.

You now have a working WordPress installation served using the Caddy web server. Caddy will automatically obtain SSL certificates from Let’s Encrypt, serve your site over a secure connection, and use HTTP/2 and Gzip compression to serve the website faster.

You can read more about Caddy and it's unique features, configuration directives for the Caddyfile in the official Caddy's website https://caddyserver.com/

## Manage MariaDB using Adminer
You can manage your MariaDB database using Adminer container that was included in the repository.

Open the web browser and enter dbadmin.example.com to open Adminer interface. Use root account and myswl_root_password to log into it.

## Remove WordPress and Cleanup
Use command ```docker-compose down``` removes the containers, but preserves your WordPress database.

Use command ```docker-compose down --volumes``` to remove everything from the server, i.e containers, network, WordPress data and MariaDB data.
