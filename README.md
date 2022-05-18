# Development environment [gabrielflores.cl](https://gabrielflores.cl)

Project created on the basis of the repository [docker-compose-lamp](https://github.com/sprintcube/docker-compose-lamp) and adapted for my personal development

## Tools and technologies used

- [Nginx](https://hub.docker.com/_/nginx)
- [Nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy)

## Prerequisities

- Install [docker](https://docs.docker.com/get-docker/)
- Install [docker-compose](https://docs.docker.com/compose/install/)

## Folder structure

- www
    - *source code of your projects*

## Installation

In a terminal enter the following command:

```bash
docker-compose build
```

After verifying that everithing is correct, run the command to make it work in the background

```bash
docker-compose up -d
```

* **Make sure you use your own custom environment variables, rename the .env_sample file to .env and modify the values**