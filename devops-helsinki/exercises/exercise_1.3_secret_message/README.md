# EXERCISE 1.3: SECRET MESSAGE

Now that we've warmed up it's time to get inside a container while it's running!

Image `devopsdockeruh/simple-web-service:ubuntu` will start a container that outputs logs into a file. Go inside the container and `use tail -f ./text.log` to follow the logs. Every 10 seconds the clock will send you a "secret message".

Submit the secret message and command(s) given as your answer.


# Solution

```bash
# spin up a container
docker container run -it \                             
                    -d \
                    --name 1.3secret_msg \
                    devopsdockeruh/simple-web-service:ubuntu
```

Let's check out the what's going on from our local machine
```bash
# follow the 
docker container logs -f <container_hashkey>
```

> Note: You can also identify the container by its name, which is more human friendly.

Output is the following, we can see that we are writing stuff to the `text.log` file
```plaintext
Starting log output
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
Wrote text to /usr/src/app/text.log
```

Now let's get inside it 
```bash
# get inside the container then run bash
docker container exec -it <container_hashkey> bash

# print out the last 5 lines of the "text.log" and follows it
tail -n 5 -f ./text.log 
```

Output is 
```
root@79b752e4bde8:/usr/src/app# tail -n 5 -f ./text.log 

2023-05-24 14:51:21 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
2023-05-24 14:51:23 +0000 UTC
2023-05-24 14:51:25 +0000 UTC
2023-05-24 14:51:27 +0000 UTC
2023-05-24 14:51:29 +0000 UTC
2023-05-24 14:51:31 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
2023-05-24 14:51:33 +0000 UTC
2023-05-24 14:51:35 +0000 UTC
2023-05-24 14:51:37 +0000 UTC
```