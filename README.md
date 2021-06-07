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

2. Check if the container is running (CONTAINER ID may differ):
```
CONTAINER ID   IMAGE               COMMAND                  CREATED         STATUS         PORTS                                                      NAMES
a686584549b7   k3s-dind_k3s-dind   "/usr/local/bin/star…"   8 minutes ago   Up 8 minutes   2375-2376/tcp, 0.0.0.0:8443->8443/tcp, :::8443->8443/tcp   k3s
```

3. With the container running retrieve the kubeconfig file from the container.
```
docker exec k3s get-kubeconfig.sh > ./k3sconfig
```

4. Set the environment variable KUBECONFIG to the location of the kube config file retrieved in the previous step.
```
$ readlink -f k3sconfig # use the path and filename returned from this command as the input for the next line
$ export KUBECONFIG=/home/$USER/$PATH_TO_REPOSITORY/$REPOSITORY_NAME/containers/k3s-dind/k3sconfig # replace this with the output of previous line
$ echo $KUBECONFIG
```

