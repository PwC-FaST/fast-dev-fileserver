# FaST file-server

Resources to setup a basic NGINX to serve static files. This is used on the FaST platform to host datasources that cannot be scraped directly.

## Install & deployment

### Docker

The actions of building, tagging and publishing Docker images can be performed using the provided Makefiles.

Execute the following bash commands in the ```file-server```directory:
1. ```make build``` to build the container image
2. ```make tag``` to tag the newly built container image
3. ```make publish``` to publish the container image on your own Docker repository.

The repository, name and tag of each Docker container image can be overridden using the environment variables DOCKER_REPO, IMAGE_NAME and IMAGE_TAG:
```bash
$> cd webapp
$> make DOCKER_REPO=index.docker.io IMAGE_NAME=eufast/file-server IMAGE_TAG=0.1.0 tag
```

### Kubernetes

A basic configuration is provided and works as is for each services. Don't forget to update the configuration according to your environment (ex: the number of replicas, docker images and ingress settings).

To deploy the file-server on Kubernetes, apply the following YAML manifests:

```bash
$> cd file-server .
$> kubectl create -f .
```

Then check the status of Kubernetes pods:

```bash
$> kubectl -n fast-platform get pod -l module=core,module=dev,app=file-server

NAME                           READY     STATUS    RESTARTS   AGE
file-server-6cd844cdc7-jssjm   1/1       Running   0          4m
```
