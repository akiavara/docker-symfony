# Docker for Symfony

This repository allows the creation of a Docker environment for setup a Symfony application

## Architecture

Here are the environment containers:

* `mysql`: [mariadb:latest](https://hub.docker.com/_/mariadb/) image.
* `nginx`: [nginx:stable](https://hub.docker.com/_/nginx/) image.
* `php`: [php:8.1.13-fpm](https://hub.docker.com/_/php/) images.

## Install

First, copy the env example file:
```
cp .env.dist .env
```

Now you can edit your `.env` with your own data:

| Variable   |      Description      |
|----------|-------------|
| WEBSITES | The path where your PHP projects are located |
| MYSQL_ALLOW_EMPTY_PASSWORD |    centered   |
| MYSQL_ROOT_PASSWORD | The password of `root` user |
| MYSQL_USER | Your mysql user |
| MYSQL_PASSWORD | The mysql user's password |
| MYSQL_DATABASE | The database name (example "projects") |

Create a Nginx file in the folder "nginx/site-available"


```
docker-compose up -d
```