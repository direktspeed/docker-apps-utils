# docker-apps-utils
Is a Bash Collection of usefull docker and docker apps as also docker-compose util functions for managing larger deployments with confidence


this is used in @dockerimages/docker-utils a image for automatic rolling upgrades of docker-apps-utils


## usage

- Create a docker-compose.yml from template
- use docker-compose.yml for creating nginx-ingress config from template


- use docker-compose.yml for creating apache2-config from template
- use docker-compose.yml for creating apache2-php config



we expect the following ENV Variables to be set so that we can support diffrent configurations

## v0 branch
```  
  HOSTNAME="$(hostname)"
  PROJECT="$(basename $PWD)"
  DOMAIN="${PROJECT}.$(hostname)"
  PROJECT_DIR="/srv/docker/$PROJECT"
  ## a git repository holding a skeleton this is for the experimental config sync algorythm
  GIT_DIR=$(dirname $(which docker-compose-sync-skel))
  USAGE="# Usage: docker-compose-env <project_name> <image_name>"
  DOCKER_IMAGE="${2:-$(docker-compose-image)}"
  DOCKER_IMAGE_TAG="$(echo $DOCKER_IMAGE | cut  -f2 -d ':')"
  CONTAINER_ENV="prod"
```

## v1 branch

```
  HOSTNAME="$(hostname)"
  PROJECT_NAME="$(basename $PWD)"
  DOMAIN="${PROJECT_NAME}.${HOSTNAME}"
  WORKING_DIR="/srv/docker" 
  PROJECT_DIR="$WORKING_DIR/$PROJECT"
  DOCKER_IMAGE="$(docker-compose-image)"
  DOCKER_IMAGE_TAG="$(echo $DOCKER_IMAGE | cut  -f2 -d ':')"
  
  ## a git repository holding a skeleton this is for the experimental config sync algorythm
  GIT_DIR=$(dirname $(which docker-compose-sync-skel))
  CONTAINER_ENV="prod"
```
