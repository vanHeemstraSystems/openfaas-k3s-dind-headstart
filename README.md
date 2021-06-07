openfaas-k3s-dind-headstart
# OpenFaas k3s dind - Headstart
- Based on "Lightweight Kubernetes inside a Docker-in-Docker container using k3s" at https://hub.docker.com/r/unboundedsystems/k3s-dind
- Based on "OpenFaas - Serverless Functions, Made Simple" at https://openfaas.com

## Prerequisites
- Docker and docker-compose
- k8s kubectl, installation instructions can be found in https://github.com/vanHeemstraSystems/k8s-kubectl
- Access to Docker Hub at https://hub.docker.com/

## k3s-dind
k3s-dind stands for the lightweight Kubernetes (k3s) Docker in Docker (dind).

## k3s
In order to create and manage a Kubernetes cluster, follow these instructions:

1. Build and run the k3s-dind container as follows:

***Option A***: using docker-compose(recommended)
```
$ cd containers/k3s-dind/
$ cp sample.docker-compose.yml docker-compose.yml
$ docker-compose up -d
```

***Option B***: using Docker run
```
$ cd containers/k3s-dind/
$ docker run -d --privileged --name k3s --hostname k3s -p 8443:8443 unboundedsystems/k3s-dind
```

2. more ...
