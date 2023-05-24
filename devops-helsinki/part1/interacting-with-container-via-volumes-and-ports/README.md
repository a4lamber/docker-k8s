# Interacting with the container via volumes and ports

Table of contents


## Interacting with volumes


## Interacting with ports

There are two ways to open a connection from outside world to a Docker container
- Exposing port `EXPOSE <port>` in your Dockerfile
- run the container with the flag `-p <host-port>:<container-port>`

let's say you have 
```
docker container run -p 4567:10000 app-in-port
```

Or you can specify a protocol by
```bash
# limit connection via udp protocol only
docker container run -p 4567:4567 app-in-port/udp
```

It is safer if you only publish your local machine's port by 
```bash
docker container run \
    -p 127.0.0.1:3456:3000
```