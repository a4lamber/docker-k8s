# EXERCISE 1.4: MISSING DEPENDENCIES

Start a Ubuntu image with the process `sh -c 'while true; do echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website; done'`

If you're on Windows, you'll want to switch the `'` and `"` around: `sh -c "while true; do echo 'Input website:'; read website; echo 'Searching..'; sleep 1; curl http://$website; done".`

You will notice that a few things required for proper execution are missing. Be sure to remind yourself which flags to use so that the container actually waits for input.

> Note also that curl is NOT installed in the container yet. You will have to install it from inside of the container.

Test inputting `helsinki.fi` into the application. It should respond with something like

```html
<html>
  <head>
    <title>301 Moved Permanently</title>
  </head>

  <body>
    <h1>Moved Permanently</h1>
    <p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
  </body>
</html>
```
This time return the command you used to start process and the command(s) you used to fix the ensuing problems.

**Hint** for installing the missing dependencies you could start a new process with `docker container exec`.

This exercise has multiple solutions, if the curl for helsinki.fi works then it's done. Can you figure out other (smart) solutions? 



# Solution

The first step is to spin up an ubuntu container and gets inside
```bash
# spin up a ubuntu
docker container run -it -d ubuntu bash

# get inside
docker exec -it 42fc47e1c46ec103d879dbad3efdf17c917a577cd07e68
66395e1d3dc477d51c bash
```


Now we are inside the container, we need to:
- update `apt-get` (good practice)
- install `curl`
- run the application
- enter the website

```bash
# update apt-get
apt-get update && apt-get upgrade -y

# install curl
apt-get install curl -y

# run the application
sh -c 'while true; do echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website; done'

# application prompts users, enter
Input website:
helsinki.fi
```

