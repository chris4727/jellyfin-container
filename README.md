# Jellyfin Server Container

This is my Jellyfin server using a docker container.

# Usage

1. Clone the repo to the local machine.
1. `cd` into the /jellyfin-container directory
1. Edit the `.env` file to contain the correct IP and media path
1. Run `docker-compose up -d` to start

# Admin

## Shell access while the container is running:

`docker exec -it jellyfin /bin/bash`

## To monitor the logs of the container in real time:

`docker logs -f jellyfin`

## Update images:

`docker-compose pull`

## Update containers:

`docker-compose up -d`

## Check installed images

`docker images`

## Remove images

`docker rmi <image_id>`


# Resources

- [Jellyfin image from linuxserver/jellyfin](https://docs.linuxserver.io/images/docker-jellyfin/#via-docker-compose)
