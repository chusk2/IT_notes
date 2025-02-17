### Run portainer (a web based docker manager)
```docker run -d -p 9000:9000 --name portainer \
  -v /var/run/docker.sock:/var/run/docker.sock \
  portainer/portainer-ce```

## Volumes

- Create and manage docker volumes
```docker volume create|inspect|ls|prune|rm vol_name```
`prune` option removes a local volume that is not in use

- List all available volumes
```docker volume ls```

- Inspect the details of a volume

```docker volume inspect vol_name```

## Ghosts blog
```docker run -d -e NODE_ENV=development -e url=http://localhost:3001 -p 3001:2368 -v ghost-vol:/var/lib/ghost/content ghost```

## Container management (once created)
```docker start|stop|restart container_id```

## Images

- remove an image

```docker rmi image_id_or_name``` 

## Networking
- disable the container's access to the network
```--network none```

## Execute commands in the container
```docker exec container_id command```
This will execute the command and return the output to the local command line

##
- Get an interactive terminal inside the container
```docker exec -it container_id /bin/sh```

- Binding a folder:
```docker run -v local_folder:container_folder <image>```

- Binding a file
```docker run -v $(pwdd)local_file_path:container_file_path <image>```
Docker expects an absolute path in the local file

## Isolating a network
Use ```-network none``` or don't define a port to forward

## Create a bridge network
Containers can communicate each other if they share the same network. At the time of running the container, set the `network` to the *bridge* network.

## Dockerfiles

```
# This is a comment

# Use a lightweight debian os
# as the base image
FROM debian:stable-slim

# execute the 'echo "hello world"'
# command when the container runs
CMD ["echo", "hello world"]
```

## Build a custom image
```docker build . -t image_name:tag```


