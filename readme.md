# Dockerized Webapp Guide + Cheatsheet

This example uses MongoDB, Node.js & Vue.js

# Dev Tools

## Windows

> - Docker UI: **Docker Desktop**
> - MongoDB UI: **MongoDB Compass**

# General

## Starting the container

- Detached mode with custom file name
    > ``docker-compose -f docker-compose.dev.yml up -d``

# Database

## Connection String

```
mongodb://takik:test-password@localhost:27017/
```

## Backup

**Volume to tarball**

- Stop the container/s first
    > ``docker-compose -f docker-compose.dev.yml  stop db``
- Create the tarball backup with a predefined name using a temporary container
    > ``docker-compose -f docker-compose.dev.yml  run --rm db-backup``
- Or create the tarball backup with a manual name
    > ``docker-compose -f docker-compose.dev.yml  run --rm -e TARGET=custom-name db-backup``

## Restore

**Tarball to volume**

- Stop the container/s first
    > ``docker-compose -f docker-compose.dev.yml  stop db``
- From a tarball backup with a predefined name using a temporary container
    > ``docker-compose -f docker-compose.dev.yml  run --rm db-restore``
- Or from a tarball backup with a manual name
    > ``docker-compose -f docker-compose.dev.yml  run --rm -e SOURCE=custom-name db-restore``
