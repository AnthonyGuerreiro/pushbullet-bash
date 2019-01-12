Base image with [pushbullet-bash](https://github.com/AnthonyGuerreiro/pushbullet-bash)

`docker run -e PB_API_KEY=<API_KEY> -it anthonyguerreiro/pushbullet-bash`

After setting up, entrypoint checks for /service and if it exists, executes it passing all args passed to *docker run* command.

If /service does not exist but args were passed, it executes them instead.

ie.:
`docker run -e PB_API_KEY=<API_KEY> -it anthonyguerreiro/pushbullet-bash /bin/sh`
having no /service, there will be a test notification, then /bin/sh is executed
