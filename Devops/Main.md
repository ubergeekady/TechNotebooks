## Docker & Kubernetes : Creating Production Grade Workflows

```
docker version
docker run hello-world

docker ps
docker ps --all

//docker run = docker create + docker start
docker run hello-world
docker create hello-world
0578a574e3c39daf428e2fcc076f01dfe48682ca5188596437103ee6f63cf8f7
docker start -a 0578a574e3c39daf428e2fcc076f01dfe48682ca5188596437103ee6f63cf8f7

//"-a" means watch for output from the container and print it out to my console
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

"-i" map our terminal to the standard IO of redis-cli

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

**We can also run a container, go inside it and manually setup. Then create an image out of the running container.**

```
docker run -it alpine sh
# apk add --update redis

docker ps
docker commit -c 'CMD ["redis-server"]' 89c37e166a23
```

## Building a Node App Image

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
FROM node:alpine //alpine is  small and compact as possible. Other ones will be larger in size. Search dockerhub.
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

**New Dockerfile with copied files**

```
FROM node:alpine
COPY ./ ./    //Current working directory to current working directory of the container.
RUN npm install
CMD ["npm", "start"]
```

```
MacBooks-MBP:simpleweb macbookpro$ docker build -t adysingh1989/simpleweb .
Sending build context to Docker daemon  4.096kB
Step 1/4 : FROM node:alpine
 ---> eaeb7e99eabd
Step 2/4 : COPY ./ ./
 ---> Using cache
 ---> 3ab2ffbffe66
Step 3/4 : RUN npm install
 ---> Using cache
 ---> 3316cf28a192
Step 4/4 : CMD ["npm", "start"]
 ---> Using cache
 ---> 78b1babf471b
Successfully built 78b1babf471b
Successfully tagged adysingh1989/simpleweb:latest
MacBooks-MBP:simpleweb macbookpro$ 
```

```
MacBooks-MBP:simpleweb macbookpro$ docker run adysingh1989/simpleweb

> @ start /
> node index.js

Listening on port 8080


```

But localhost:8080 wont work. 

Container port mapping.

If someone sends a request to my computer on port 8080, map it to port 8080 of the container.

We do not setup port forwarding in the Dockerfile. It is a runtime thing.

```
//To go inside the shell of the container and not run the default command
docker run -it adysingh1989/simpleweb sh
```

```
macbookpro$ docker run -p 8080:8080 adysingh1989/simpleweb
```

```
FROM node:alpine
WORKDIR /usr/app
COPY ./ ./
RUN npm install
CMD ["npm", "start"]
```

```
docker build -t adysingh1989/simpleweb .
docker run -p 8080:8080 adysingh1989/simpleweb

docker exec -it ba804b107b57 sh

/usr/app # ls
Dockerfile         index.js           node_modules       package-lock.json  package.json
/usr/app # 
```



## Using Docker-Compose to Setup 2 linked containers

**index.js**

```js
const express = require('express');
const redis = require('redis');

const app = express();
const client = redis.createClient();
client.set('visits', 0);

app.get('/', (req, res) => {
  client.get('visits', (err, visits) => {
    res.send('Number of visits is ' + visits);
    client.set('visits', parseInt(visits) + 1);
  });
});

app.listen(8081, () => {
  console.log('Listening on port 8081');
});
```

**package.json**

```json
{
  "dependencies": {
    "express": "*",
    "redis": "2.8.0"
  },
  "scripts": {
    "start": "node index.js"
  }
}
```

**Dockerfile**

```
FROM node:alpine
WORKDIR /usr/app
COPY ./package.json ./
RUN npm install
COPY ./ ./
CMD ["npm", "start"]
```

Start redis container

```
docker run redis
```

Better to use docker-compose. 

docker-compose.yml

```yaml
version: '3'
services: 
  redis-server:
    image: 'redis'
  node-app:
    build: .
    ports:
      - "4001:8081"
```

Docker compose will have both services free access to each other.

**index.js again**

```js
const client = redis.createClient({
	host: 'redis-server',
	port: 6379
});
```

```
docker-compose up --build
docker-compose down
docker-compose ps
```

Restart policies

```
version: '3'
services: 
  redis-server:
    image: 'redis'
  node-app:
  	restart: always
    build: .
    ports:
      - "4001:8081"
```

```
restart: "no"
restart: always
restart: on-failure
restart: unless-stopped
```

## Creating Production Grade Workflows (React Example)

```
create-react-app frontend
cd frontend
npm run test
npm run build
npm run serve
```

create new Dockerfile.dev (for development environment)

```
FROM node:alpine
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "run", "start"]
```

```
docker build -f Dockerfile.dev .
```

Might want to delete node_modules to make it smaller (can be reinstated with npm install)

```
docker run -p 3000:3000 3f745de211a3
```

Goto localhost. Phew

Edit open src/app.js and edit some text. Refresh the localhost. But it won't update.

Docker volume, we are essentially setting up a mapping from a folder inside the container to a file or folder outside the container.

```
docker run -p 3000:3000 -v $(pwd):/app 057bd5c72ec1
```

This should throw an error. The node_modules folder inside the container got overriden by this mapping.

```
docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app 196ba1d36130
```

The -v command without the colon mapping means don't try to map that particular folder.

