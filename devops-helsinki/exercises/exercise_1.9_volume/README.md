# EXERCISE 1.9: VOLUMES

In this exercise we won't create a new Dockerfile.

Image `devopsdockeruh/simple-web-service` creates a timestamp every two seconds to `/usr/src/app/text.log` when it's not given a command. Start the container with bind mount so that the logs are created into your filesystem.

Submit the command you used to complete the exercise.

Hint: read the note that was made just before this exercise!


# Solution

Recall the command, we could define our volume like this.

```bash
docker container run -v <host_path>:<container_path> <image_name>
```

Since the image for this exercise is not available for `arm64`, let's use ubuntu as an example to illustrate bind mount

```bash
# create a container with bind mount
docker container run -it \
            -v $(pwd):/usr \
            ubuntu:18.04
```

The above could will mount the current directory with the `<container>:/usr` directory.


