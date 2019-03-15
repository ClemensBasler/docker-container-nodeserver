# My notebook for handling with docker
This project runs a simple node server. Its made as a personal reminder how to handle with docker. The first example is

generic, the second an example. Before building the container no npm i is needed, because Docker does it by itself,

as it can seen in the Dockerfile.

### Pulling, Running, Building and Pushing the Docker Container

<b>logging in </b>

- docker login (server)

The standard docker login refers to the [Docker Cloud](https://cloud.docker.com/)

<b>building:</b>

- docker build -t [Docker Cloud Name]/[favored container name]:[tag] [location]

- docker build -t clemensbasler/nodeserver-dockercontainer:latest .

<b>pushing</b>

- docker push [imagename]

- docker push clemensbasler/nodeserver-dockercontainer:latest

<b>running:</b>

- docker run [options] [image]

- docker run --net="host" clemensbasler/nodeserver-dockercontainer:latest

The --net="host" option is needed, that the container can access to the network ports of the host

<b>pulling:</b>

- docker pull [imagename]

- docker pull clemensbasler/nodeserver-dockercontainer:latest

### Other useful Docker commands

<b>shows all images (default hides intermediate images):</b>
- docker images -a

<b>shows running docker container:</b>
- docker ps

<b>shows all docker container:</b>
- docker ps -a

<b>deletes a Container:</b>
- docker rm [Container ID]

<b>deletes all unused Containers:</b>
- docker rm \`docker ps -aq\`

<b>deletes Image:</b>
- docker rmi [Image ID]

<b>deletes all images tagged with <none> (but the one with "dependent child images"):</b>
- docker rmi $(docker images -a | grep "^<none>" | awk '{print $3}')

<b>stop an running container/image</b>
- docker stop [Container ID]

### Docker behind a proxy

Add to the ~/.docker/config.json file the proxy settings:

```json
{
 "proxies":
 {
   "default":
   {
     "httpProxy": "http://127.0.0.1:3001",
     "httpsProxy": "http://127.0.0.1:3001",
     "noProxy": "*.test.example.com,.example2.com"
   }
 }
}
```
