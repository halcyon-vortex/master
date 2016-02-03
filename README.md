# master

## Team

  - __Product Owner__: Devin Pastoor
  - __Dev Ops / Scrum Master__: Ben Balaran
  - __Developer__: Spencer Ochs

## Microservices

  - __Front-End Server__
  - __Back-End Server__
  - __In-Memory Storage__
  - __Database__

### Install Procedure

```
git clone --recursive https://github.com/halycon-vortex/master
```



### Run inside of docker:

In Terminal from within root directory:
```sh
docker-machine start <machine-name>
eval "$(docker-machine env <machine-name>)"
docker pull ubuntu
docker pull node
docker pull redis
docker-compose up
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

###Docker Image Build Requests

Send post request in the following format:
```
curl -H "Content-Type: application/json" --data '{"build": true}' -X POST <auto-build-link>
```
Insert the following links to specify the build:

> Front-end-server : https://registry.hub.docker.com/u/bbalaran/front-end-server/trigger/519d5267-d92b-4e65-96ad-3362fdac26f9/
> Back-end-server : https://registry.hub.docker.com/u/bbalaran/back-end-server/trigger/a99ed444-d2a3-4b16-922a-d4ef98ae62bc/
> In-Memory-Storage : https://registry.hub.docker.com/u/bbalaran/in-memory-storage/trigger/9a0dbbc4-9764-4861-9ab3-7c7964f91e23/
> Database : https://registry.hub.docker.com/u/bbalaran/database/trigger/2fd3900f-d93e-48bd-89b9-30b39949d8af/

