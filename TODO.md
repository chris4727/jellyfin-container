# TODO

## Add a Docker entrypoint

To ensure Docker waits until your encrypted volume is unlocked before running, you can use a combination of Docker Compose’s depends_on and a custom entrypoint script. Here’s a step-by-step guide:

1. Create a custom entrypoint script: This script will check if the volume is unlocked before proceeding.

```
    #!/bin/bash
    while [ ! -d /path/to/your/volume ]; do
      echo "Waiting for volume to be unlocked..."
      sleep 5
    done
    exec "$@"
```

1. Save this script as entrypoint.sh and make it executable:

```
    chmod +x entrypoint.sh
```

1. Update your docker-compose.yml: Modify your service to use the custom entrypoint script.

```
    version: '3.8'
    services:
      your_service:
        image: your_image
        volumes:
          - /path/to/your/volume:/container/path
        entrypoint: ["/path/to/entrypoint.sh"]
        depends_on:
          - another_service
```

    Ensure the volume is unlocked before starting Docker Compose: You can add a check in your system startup scripts or manually unlock the volume before running docker-compose up.

This setup ensures that Docker Compose will wait until the volume is available before starting the service.

# Set up hardware acceleration

From <https://hub.docker.com/r/linuxserver/jellyfin>

To leverage hardware acceleration you will need to mount /dev/dri video device inside of the container.

`--device=/dev/dri:/dev/dri`

