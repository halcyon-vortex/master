# Github Compass

## Overview
Github Compass provides a platform for discovery of new and exciting open-source projects on Github. Github is a flourishing community with contributors innovating in countless languages and practices, and discovering new technologies and tools can be a daunting task.

Github Compass provides the solution with algorithms to show trending repositories that are both newer and well-established, across any and all programming languages.

We achieved this by creating a snapshot of github from https://www.githubarchive.org/ log data. Our database is regularly updated with new logs, and uses a weighting algorithm to determine current trends in repositories.

For more information on our system architecture and deployment flow, see the diagrams attached in this repository.

## Team

  - __Product Owner__: Devin Pastoor
  - __Dev Ops / Scrum Master__: Ben Balaran
  - __Developer__: Spencer Ochs

## Microservices
The application is built on a micro-service architecture leveraging docker. This allows all the separate services to reside in separate repositories.
  - __Front-End Server:__ NGINX server and load balancer
  - __Back-End Server:__ Node cluser, server-side rendering and client directory
  - __In-Memory Storage:__ Redis cache
  - __Database:__ Postgres
  - __Service-worker:__ Python service worker to populate Redis from Postgres

### Install Procedure
To initialize and update all submodules to the proper branch locally
```sh
git clone --recursive https://github.com/halycon-vortex/master
git submodule foreach git pull origin master
```



### Run inside of docker:

In Terminal from within root directory:
You can either pull down the base images separately, or they will be pulled down as docker-compose is run
```sh
docker-machine start <machine-name>
eval "$(docker-machine env <machine-name>)"
docker pull ubuntu:latest
docker pull node:latest
docker pull redis:latest
docker pull python:latest
docker pull postgres:9.4.3
docker-compose up
```
Use the following commands to populate the database with the seed data
```sh
docker exec -it master_postgres_1 bash
psql -U postgres test-db < /tmp/psql_data/december_v3_2015_02_08
```
Use the following commands to activate python worker to load redis cache
```sh
docker run --link master_redis1:redis --link master_postgres_1:postgres master_python-worker <number> <day/week/month>
```

### Run server outside of docker:

In Terminal:
```sh
brew install redis
redis-server
```

From within the Back-End-Server directory:

```sh
npm install
npm start
```


If submodules cannot be found, check the submodule branches and ensure they are on heads/master:

```
git submodule status
git submodule foreach git checkout master
```
