 # hub.docker.com/tiredofit/postgres

[![Build Status](https://img.shields.io/docker/build/tiredofit/postgres.svg)](https://hub.docker.com/r/tiredofit/postgres)
[![Docker Pulls](https://img.shields.io/docker/pulls/tiredofit/postgres.svg)](https://hub.docker.com/r/tiredofit/postgres)
[![Docker Stars](https://img.shields.io/docker/stars/tiredofit/postgres.svg)](https://hub.docker.com/r/tiredofit/postgres)
[![Docker Layers](https://images.microbadger.com/badges/image/tiredofit/postgres.svg)](https://microbadger.com/images/tiredofit/postgres)
[![Image Size](https://img.shields.io/microbadger/image-size/tiredofit/postgres.svg)](https://microbadger.com/images/tiredofit/postgres)

# Introduction

Dockerfile to build a [Postgres Server](https://postgres.org) Image.
It has the same configuration variables as the Official [Postgres Image](https://github.com/docker-library/postgres)

* This Container uses a [customized Alpine Linux base](https://hub.docker.com/r/tiredofit/alpine) which includes [s6 overlay](https://github.com/just-containers/s6-overlay) enabled for PID 1 Init capabilities, [zabbix-agent](https://zabbix.org) based on TRUNK compiled for individual container monitoring, Cron also installed along with other tools (bash,curl, less, logrotate, postgres-client, nano, vim) for easier management. It also supports sending to external SMTP servers..


[Changelog](CHANGELOG.md)

# Authors

- [Dave Conroy](https://github.com/tiredofit)

# Table of Contents

- [Introduction](#introduction)
    - [Changelog](CHANGELOG.md)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
    - [Database](#database)
    - [Data Volumes](#data-volumes)
    - [Environment Variables](#environmentvariables)   
    - [Networking](#networking)
- [Maintenance](#maintenance)
    - [Shell Access](#shell-access)
   - [References](#references)

# Prerequisites


# Installation

Automated builds of the image are available on [Docker Hub](https://hub.docker.com/tiredofit/postgres) and is the recommended method of installation.


```bash
docker pull hub.docker.com/tiredofit/postgres
```

The following image tags are available:

* `9.5:latest` - Alpine 3.5 - Postgres 9.5
* `9.6:latest` - Alpine 3.5 - Postgres 9.6
* `10:latest` - Alpine 3.5 - Postgres 10
* `latest` - Alpine 9.5

# Quick Start

* The quickest way to get started is using [docker-compose](https://docs.docker.com/compose/). See the examples folder for a working [docker-compose.yml](/docker/postgres/examples/docker-compose.yml) that can be modified for development or production use.

* Set various [environment variables](#environment-variables) to understand the capabilities of this image.
* Map [persistent storage](#data-volumes) for access to configuration and data files for backup.

# Configuration

### Data-Volumes

The following directories are used for configuration and can be mapped for persistent storage.

| Directory | Description |
|-----------|-------------|
| `/var/lib/postgresql/data` | Postgres Data Directory |



### Environment Variables

Along with the Environment Variables from the [Base image](https://hub.docker.com/r/tiredofit/alpine), below is the complete list of available options that can be used to customize your installation.

| Parameter | Description |
|-----------|-------------|
| `PG_DATA` | Location for Data Storage - Default `/var/lib/postgresql/data` |
| `POSTGRES_DB` | Optional - Automatically Create Database (e.g. database) |
| `POSTGRES_USER` | Optional - Automatically Assign Username Priveleges to Database (e.g. user) |
| `POSTGRES_PASSWORD` | Password for authentication to above database (e.g. userpassword) |
| `POSTGRES_INITDB_ARGS` | Send arguments to postgres-initdb (e.g. `--data-checksums`) |
| `POSTGRES_INITDB_XLOGDIR | Optional Log Location - Default `/var/lib/postgresql/data` |


### Networking

The following ports are exposed.

| Port      | Description |
|-----------|-------------|
| `5432` 	   	| Postgres Server | 		    |

# Maintenance
#### Shell Access

For debugging and maintenance purposes you may want access the containers shell. 

```bash
docker exec -it (whatever your container name is e.g. postgres) bash
```

# References

* https://postgres.org


