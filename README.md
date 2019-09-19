[PostgreSQL](https://www.postgresql.org/) is an open source relational database system.

This docker-compose config is intended to be used by other docker services,
using my [base docker services](https://github.com/StarlitGhost/selfhost-base).

Other services I run that currently use this:
 - [ttrss](https://github.com/StarlitGhost/selfhost-ttrss) RSS Reader
 - [gitea](https://github.com/StarlitGhost/selfhost-gitea) Git Repository Host

This docker config uses [this image](https://hub.docker.com/_/postgres)

# Setup

This relies on my [base docker services](https://github.com/StarlitGhost/selfhost-base).  
You'll want to symlink that project's .env file into this project's directory
and set `POSTGRES_USER` and `POSTGRES_PW` in it.

Next create a docker network for containers that want to use postgres:

`docker network create postgres_network`

Once that's done you can just spin it up with `docker-compose up -d`.

You'll need to create a database for each project that uses this;
those instructions are in each repository's README,
but generally involve running something like this once the postgres container is running:

`docker exec -it postgres createdb -U docker db-name`
