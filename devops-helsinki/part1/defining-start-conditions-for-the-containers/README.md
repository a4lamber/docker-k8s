# Defining start conditions for the container

- [Defining start conditions for the container](#defining-start-conditions-for-the-container)
  - [Steps to write a Dockerfile](#steps-to-write-a-dockerfile)
  - [Difference between ENTRYPOINT and CMD](#difference-between-entrypoint-and-cmd)
  - [Shell form and exec form for `CMD` and `ENTRYPOINT`](#shell-form-and-exec-form-for-cmd-and-entrypoint)


## Steps to write a Dockerfile

Three steps to write a Dockerfile:
- spin up a test container of your base image
- do your configurations and set-up inside the test container
- write your Dockerfile


## Difference between ENTRYPOINT and CMD


|command|description|-|
|---|---|---|
|`CMD`|specifies the default command to run when the container is started.|-|
|`ENTRYPOINT`|specifies the command to be run when the container is started, and any additional arguments specified when running the container will be passed as arguments to the `ENTRYPOINT` command|-|

Recall the `docker container run` command
```bash
docker container run [OPTIONS] IMAGE [COMMAND] [ARG...]
```

By default, passing in command and arg are optional. It is because the image has been defined with `CMD` or `ENTRYPOINT`.

If both `CMD` and `ENTRYPOINT` are defined, `ENTRYPOINT` becomes command while `CMD` becomes argument.

## Shell form and exec form for `CMD` and `ENTRYPOINT`

not important for now.