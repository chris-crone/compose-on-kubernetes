# Compose on Kubernetes

[![CircleCI](https://circleci.com/gh/docker/compose-on-kubernetes/tree/master.svg?style=svg)](https://circleci.com/gh/docker/compose-on-kubernetes/tree/master)

Compose on Kubernetes allows you to deploy Docker Compose files onto a
Kubernetes cluster.

# Get started

Compose on Kubernetes comes installed on
[Docker Desktop](https://www.docker.com/products/docker-desktop) and
[Docker Enterprise](https://www.docker.com/products/docker-enterprise).

On Docker Desktop you will need to activate Kubernetes in the settings to use
Compose on Kubernetes.

To deploy a stack, you can use the Docker CLI:

```console
$ cat docker-compose.yml
version: '3.3'

services:

  db:
    build: db
    image: dockersamples/k8s-wordsmith-db

  words:
    build: words
    image: dockersamples/k8s-wordsmith-api
    deploy:
      replicas: 5

  web:
    build: web
    image: dockersamples/k8s-wordsmith-web
    ports:
     - "33000:80"

$ docker stack deploy --orchestrator=kubernetes -c docker-compose.yml hellokube
```

# Developing Compose on Kubernetes

See the [debugging](./DEBUGGING.md) and [contributing](./CONTRIBUTING.md)
guides.
