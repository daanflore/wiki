At the moment Podman and docker still use the same commands so you can define an alias for it
# Build container

``` shell
# Based on the current folder build a container using dockerfile
podman build . --tag squid
```


# Run container
``` shell
# --network=host => allows container to be available from the host
# --rm  => Automatically remove the container and any anonymous unnamed volume associated with the container when it exits. The default is **false**.
# --name => name of the container
# localhost/squid => where to find image and image to use
podman run --network=host --rm --name squid localhost/squid
```

# Enter container in bash 
```shell
# -i => interactive
# -t => allow interactive shell
# squid => name of container
# bash => shell to use
podman exec -it squid bash
```