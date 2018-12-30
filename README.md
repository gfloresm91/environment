# Entorno de desarrollo [gabrielflores.cl](https://gabrielflores.cl)

Proyecto creado siguiendo la base del repositorio [docker-compose-lamp](https://github.com/sprintcube/docker-compose-lamp) y adaptado para mi desarrollo personal.

## Herramientas y tecnologías utilizadas

- Docker
- Docker compose
- Ubuntu server
- Apache2
- PHP
- Mysql
- Letsencrypt
- PHPMyAdmin
- Redis
- .Net Core
- Microsoft Sql Server Core

## Pre-requisitos

- Instalar docker
- Dentro de la carpeta **netcore** deben estar las fuentes del proyecto asp.net core creadas con el comando **dotnet publish**

## Estructura de carpetas

Debe quedar el siguiente árbol de directorios

- bin
    - dotnetcore
    - mysql
    - webserver
- config
    - apache
    - letsencrypt
    - nextcloud
    - php
    - vhosts
- data
    - mssql
    - mysql
- logs
    - apache2
    - gitlab
    - mssql
    - mysql
    - openproject
- www
    - netcore
    - nextcloud
    - *Las fuentes de tus proyectos*

## Instalación

En una terminal se debe ingresar el siguiente comando:

```bash
docker-compose build
```

Luego de verificado que esta todo correcto, ejecutas el comando para que funcione en background

```bash
docker-compose up -d
```

* **Asegurate de utilizar tus propias variables de entorno personalizadas, renombra el archivo .env_sample a .env y modifica los valores**