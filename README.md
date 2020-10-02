# Gitea Dockerized

- [Gitea Dockerized](#gitea-dockerized)
  - [Overview](#overview)
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)

---

## Overview

This repository contains a template to deploy [Gitea](https://gitea.io/) using [Docker Compose](https://docs.docker.com/compose/) on a single machine running [Docker](https://www.docker.com/).

## Requirements

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Git](https://git-scm.com/)
- Text editor of your choice (e.g. [Vim](https://www.vim.org/))

## Installation

Clone the repository:

```sh
$ git clone https://github.com/cedrichopf/gitea-dockerized.git
Cloning into 'gitea-dockerized'...
```

Create a copy of the example configuration files:

```sh
# Gitea Configuration
$ cp example.env .env
# Custom Docker Compose Configuration
$ cp override.example.yml docker-compose.override.yml
```

Configure the Gitea deployment by adapting the environment variables in the `.env` file:

```sh
$ vim gitea.env
```

Further information about the available environment variables can be found here: [Environment Variables](#environment-variables)

Configure the docker-compose.override.yml file:

```sh
$ vim docker-compose.override.yml
```

**Important:** The example configuration doesn't publish any ports by default. It uses an existing [Traefik](https://containo.us/traefik/) instance as a reverse proxy to access the Gitea instance. If you want to publish ports, please add them to the `docker-compose.override.yml` configuration.

Download the Docker images and start the services using docker-compose:

```sh
$ docker-compose pull
$ docker-compose up -d
```

Open your browser and access your Gitea instance using the URL of the Docker host and the configured route, e.g. [http://127.0.0.1](http://127.0.0.1).

## Environment Variables

The following table contains an overview of the environment variables which can be configured in the `gitea.env` file.

| Environment Variable | Example            | Description                     |
| -------------------- | ------------------ | ------------------------------- |
| COMPOSE_PROJECT_NAME | `gitea`            | Project name for docker-compose |
| POSTGRES_USER        | `gitea`            | Username of the database user   |
| POSTGRES_PASSWORD    | `s5xwMGLPh2qfDEVu` | Password of the database user   |
| POSTGRES_DB          | `gitea`            | Name of the database            |
