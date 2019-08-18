```
docker version
docker run hello-world

docker ps
docker ps --all

docker run = docker create + docker start
docker create hello-world
0578a574e3c39daf428e2fcc076f01dfe48682ca5188596437103ee6f63cf8f7
docker start -a 0578a574e3c39daf428e2fcc076f01dfe48682ca5188596437103ee6f63cf8f7

-a means watch for output from the container and print it out to my console
```

```
docker run busybox echo hi there
hi there
docker ps -all
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
6daa2179a90f        busybox             "echo hi there"     8 seconds ago       Exited (0) 7 seconds ago                       cocky_snyder

docker start -a 6daa2179a90f
hi there


docker system prune
//Will delete all the containers
```

```
docker create busybox echo hi there
74324559e2897ecda6a43b05a10cd4b0130c5480c0838fdbc95ea0644d41c406

docker start 74324559e2897ecda6a43b05a10cd4b0130c5480c0838fdbc95ea0644d41c406
74324559e2897ecda6a43b05a10cd4b0130c5480c0838fdbc95ea0644d41c406

docker logs 74324559e2897ecda6a43b05a10cd4b0130c5480c0838fdbc95ea0644d41c406
hi there
```

**Docker stop / Docker kill**

Stop is graceful shutdown and kill is just kill

```
docker run redis

Running redis-cli inside the container

docker exec -it f6948fdbee56 redis-cli

-i map our terminal to the standard IO of redis-cli

docker exec -it f6948fdbee56 sh
#cd /
#ls
bin  boot  data  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

docker run -it busybox sh
#
```

## Creating Docker Images

```
mkdir redis-image
cd redis-image
touch Dockerfile
```

**DockerFile**

```
# Use an existing docker image as a base
FROM alpine

# Download and install a dependency
RUN apk add --update redis

# What to do when it starts as a container
CMD ["redis-server"]
```

```
docker build .
Successfully built 78795007f37d
docker run 78795007f37d

To naming/tagging the build

docker build -t adysingh1989/redis:latest .
docker run adysingh1989/redis
```

**We can also run a container, go inside it and manually setup. Then create an image out of the container.**

```
docker run -it alpine sh
# apk add --update redis

docker ps
docker commit -c 'CMD ["redis-server"]' 89c37e166a23
```

## Building a Node Repository

**package.json**

```json
{
	"dependencies": {
		"express": "*"
	},
	"scripts": {
		"start": "node index.js"
	}
}
```

**index.js**

```go
const express = require('express')

const app = express();

app.get('/', (req, res) => {
	res.send('Hi, there');
});

app.listen(8080, () =>{
	console.log("Listening on port 8080")
});
```

**Dockerfile**

```
FROM node:alpine //alpine is the small and compact as possible. Other ones will be larger in size
RUN npm install
CMD ["npm", "start"]
```

```
MacBooks-MBP:simpleweb macbookpro$ docker build .
Sending build context to Docker daemon  4.096kB
Step 1/3 : FROM node:alpine
alpine: Pulling from library/node
e7c96db7181b: Pull complete 
3c504dd883c7: Pull complete 
391efc267ebb: Pull complete 
ffe3d971af22: Pull complete 
Digest: sha256:9b4ef9aae0d8c9c7a4dbbff596acf98e7d7e6a1843ed7d751fabfc2d4680a5d5
Status: Downloaded newer image for node:alpine
 ---> eaeb7e99eabd
Step 2/3 : RUN npm install
 ---> Running in 85d84254e0d1
npm WARN saveError ENOENT: no such file or directory, open '/package.json'
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN enoent ENOENT: no such file or directory, open '/package.json'
npm WARN !invalid#2 No description
npm WARN !invalid#2 No repository field.
npm WARN !invalid#2 No README data
npm WARN !invalid#2 No license field.

up to date in 1.61s
found 0 vulnerabilities

Removing intermediate container 85d84254e0d1
 ---> 194d30ac276b
Step 3/3 : CMD ["npm", "start"]
 ---> Running in 6f6cdd38ae93
Removing intermediate container 6f6cdd38ae93
 ---> 272b67e2d712
Successfully built 272b67e2d712
MacBooks-MBP:simpleweb macbookpro$ 
```

