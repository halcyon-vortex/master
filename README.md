# master

## Team

  - __Product Owner__: Devin Pastoor
  - __Scrum Master__: Ben Balaran
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
