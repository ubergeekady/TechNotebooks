## <u>Devops Workshop Notes</u>

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

**Using Docker Compose** for the same thing.

We need to specify context to tell where to pull all the files from.

The location of the docker file

```yaml
version: '3'
services:
  web:
    build:
      context: .
      dockerfile: Dockerfile.dev
    ports: 
      - "3000:3000"
    volumes:
      - /app/node_modules
      - .:/app
```

[COPY . .] in dockerfile is not necessary for this particular case .... but better leave it.

**For running tests inside our container**

```
docker build -f Dockerfile.dev .
docker run 9acc046e166c npm run test

//won't work
//add -it tag

docker run 9acc046e166c npm run test
```

Now go to src/app.test.js and make changes to it. This won't update the running test menu. It is because the container contains old files. We didn't setup the volume thing which we did in this tutorial a bit earlier.

One approach to this is -

```
docker ps -all
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
ff46c46d467a        frontend_web        "docker-entrypoint.s…"   16 seconds ago      Created                                 frontend_web_1


docker exec -it ff46c46d467a npm run test
```

The other approach -

Docker-compose

```yaml
version: '3'
services:
  web:
    build:
      context: .
      dockerfile: Dockerfile.dev
    ports: 
      - "3000:3000"
    volumes:
      - /app/node_modules
      - .:/app

  tests:
    build:
      context: .
      dockerfile: Dockerfile.dev
    volumes:
      - /app/node_modules
      - .:/app
    command: ["npm", "run", "test"]
```

```
docker-compose up --build
```

This should start two containers - one with test and one is the main one

Try changing the test suite file

This second approach also has some problems - you don't have interactivity with the test runner.

You might go to a new window and do a "docker attach" to the container (using docker ps). But it won't work. Why ?

Go into the tests container with "docker exec -it d59aa30f69fd sh" and do "ps". There are two "npm test" processes inside. Docker attach will attach to STD/IO/ERR of the main process.

This is not possible in docker. So the second approach won't work as well.

**Dockerfile for production**

Only the build folder generated by "npm build" needs to go along with nginx.

We can use the nginx base image.

Multi-staged build process required.

Production Dockerfile

```
FROM node:alpine AS builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
```

## Continuous Integration & Deployment with TravisCI & AWS

```
git init
git commit -m "initial commit"
git remote add origin https://github.com/ubergeek89/docker-react.git
git push -u origin master
```

Create the .travis.yml file

```yaml
sudo: required
services:
  - docker

before_install:
  - docker build -t adysingh1989/docker-react -f Dockerfile.dev .

script:
  - docker run -e CI=true adysingh1989/docker-react npm run test
```

**Making Travis auto-deploy to AWS beanstalk**

Goto Elastic Beanstalk and create new application with name : docker-react >> Create new environment >> Web server environment >> Platform : Docker >> Create and then wait

Create IAM secret keys with permissions to elastic beanstalk

Put the config like such

```yaml
sudo: required
services:
  - docker

before_install:
  - docker build -t adysingh1989/docker-react -f Dockerfile.dev .

script:
  - docker run -e CI=true adysingh1989/docker-react npm run test

deploy:
  provider: elasticbeanstalk
  region: "us-east-2"
  app: "docker-react"
  env: "DockerReact-env"
  bucket_name: "elasticbeanstalk-us-east-2-509296601184"
  bucket_path: "docker-react"
  on:
    branch: master
  access_key_id: $AWS_ACCESS_KEY
  secret_access_key: 
    secure: "$AWS_SECRET_KEY"
```

Expose port 80 in the production Dockerfile

```
FROM node:alpine AS builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 80
COPY --from=builder /app/build /usr/share/nginx/html
```

Create a new branch on your machine

```
git checkout -b feature
```

change the code and then add and commit and push it to the feature branch

```
git push origin feature
```

Goto github and create pull request. Travis-CI will kick in.

## Dockerizing Multiple Services

Use the React/Node app in Checkpoint.zip which has client, server and worker folders

**client/Dockerfile.dev**

```
FROM node:alpine
WORKDIR './app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run","start"]
```

**server/Dockerfile.dev**

```
FROM node:alpine
WORKDIR './app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run","dev"]
```

**worker/Dockerfile.dev**

```
FROM node:alpine
WORKDIR './app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run","dev"]
```

```
//Do it for all of the above
docker build -f Dockerfile.dev .
```

**NGinx Container**

/nginx/default.conf

```
upstream client {
	server client:3000;
}

upstream api{
	server api:5000;
}

server {
	listen 80;

	location / {
		proxy_pass http://client;
	}

	location /api {
		rewrite /api/(.*) /($1) break;
		proxy_pass http://api;
	}
}
```

docker-compose.yml

```yaml
version: '3'
services:
  postgres:
    image: 'postgres:latest'
  redis:
    image: 'redis:latest'
  nginx:
    restart: always
    build:
      dockerfile: Dockerfile.dev
      context: ./nginx
    ports:
      - '3050:80'
  api:
    build:
      dockerfile: Dockerfile.dev
      context: ./server
    volumes:
      - /app/node_modules
      - ./server:/app
    environment:
      - REDIS_HOST=redis
      - REDIS_PORT=6379
      - PGUSER=postgres
      - PGHOST=postgres
      - PGDATABASE=postgres
      - PGPASSWORD=postgres_password
      - PGPORT=5432
  client:
    build:
      dockerfile: Dockerfile.dev
      context: ./client
    volumes:
      - /app/node_modules
      - ./client:/app
  worker:
    build:
      dockerfile: Dockerfile.dev
      context: ./worker
    volumes:
      - /app/node_modules
      - ./worker:/app
```

## CI Workflow for multiple images

Create production dockerfile in worker and server folders with npm start command (only difference).

Dockerfile for nginx folder will be the same

Dockerfile for client folder

```
FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
```

client/nginx (another nginx for serving client/react static files)

client/nginx/default.conf

```
server {
  listen 3000;
 
  location / {
    root /usr/share/nginx/html;
    index index.html index.htm;
    try_files $uri $uri/ /index.html;  <<------Add this!!!!
  }
}
```

Push to github.

**.travis.yml**

```yaml
sudo: required
services:
  - docker

before_install:
  - docker build -t adysingh1989/react-test -f ./client/Dockerfile.dev ./client

script:
  - docker run -e CI=true adysingh1989/react-test npm test -- --coverage

after_success:
  - docker build -t adysingh1989/multi-client ./client
  - docker build -t adysingh1989/multi-nginx ./nginx
  - docker build -t adysingh1989/multi-server ./server
  - docker build -t adysingh1989/multi-worker ./worker
  - echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_ID" --password-stdin
  - docker push adysingh1989/multi-client
  - docker push adysingh1989/multi-nginx
  - docker push adysingh1989/multi-server
  - docker push adysingh1989/multi-worker
```

## Multi-Container Deployment To AWS Elastic Container Service

**Dockerrun.aws.json**

```json
{
	"AWSEBDockerrunVersion": 2,
	"containerDefinitions": [
		{
			"name": "client",
			"image": "adysingh1989/multi-client",
			"hostname": "client",
			"essential": false,
      "memory": 128
		},
		{
			"name": "server",
			"image": "adysingh1989/multi-server",
			"hostname": "api",
			"essential": false,
      "memory": 128
		},
		{
			"name": "worker",
			"image": "adysingh1989/multi-worker",
			"hostname": "worker",
			"essential": false,
      "memory": 128
		},
		{
			"name": "nginx",
			"image": "adysingh1989/multi-nginx",
			"hostname": "nginx",
			"essential": true,
			"portMappings": [
				{
					"hostPort": 80,
					"containerPort": 80
				}
			],
			"links": ["client", "server"],
      "memory": 128
		}
	]
}
```

Goto Elastic Beanstalk and create new application with name : docker-react >> Create new environment >> Web server environment >> Platform : "MultiContainer Docker" >> Create and then wait

Create IAM secret keys with permissions to elastic beanstalk.

There is one VPC for every zone. Go to VPC dashboard in AWS. There is default VPC for every region.

Create a security group/firewall rules. There will be one created for the EBS environment. Click on it. Goto inbound rules. 

Goto RDS -> Create DB -> Postgres >> Put the instance identifier, username, password.

Create Redis ElasticCache

Create new security group. Apply to all resources.

Setup environment variables in AWS console

```
REDIS_HOST=<url>
REDIS_PORT=6379
PGUSER=postgres
PGHOST=<url>
PGDATABASE=fibvalues
PGPASSWORD=postgrespassword
PGPORT=5432
```

All containers will automatically have access to the environment variables.

##### AWS Configuration Cheatsheet

AWS Configuration Cheat Sheet

This lecture note is not intended to be a replacement for the videos, but only to serve as a cheat sheet for students who want to quickly run thru the AWS configuration steps or easily see if they missed a step. Steps listed are accurate as of 7-11-2019, keep in mind that AWS makes frequent small changes to their UI.

**RDS Database Creation**

1. Go to AWS Management Console and use Find Services to search for RDS
2. Click Create database button
3. Select PostgreSQL
4. Check 'only enable options eligible for RDS Free Usage Tier' and click Next button
5. Scroll down to Settings Form
6. Set DB Instance identifier to multi-docker-postgres
7. Set Master Username to postgres
8. Set Master Password to postgres and confirm
9. Click Next button
10. Make sure VPC is set to Default VPC
11. Scroll down to Database Options
12. Set Database Name to fibvalues
13. Scroll down and click Create Database button

**ElastiCache Redis Creation**

1. Go to AWS Management Console and use Find Services to search for ElastiCache
2. Click Redis in sidebar
3. Click the Create button
4. Make sure Redis is set as Cluster Engine
5. In Redis Settings form, set Name to multi-docker-redis
6. Change Node type to 'cache.t2.micro'
7. Change Number of replicas to 0
8. Scroll down to Advanced Redis Settings
9. Subnet Group should say “Create New"
10. Set Name to redis-group
11. VPC should be set to default VPC
12. Tick all subnet’s boxes
13. Scroll down and click Create button

**Creating a Custom Security Group**

1. Go to AWS Management Console and use Find Services to search for VPC
2. Click Security Groups in sidebar
3. Click Create Security Group button
4. Set Security group name to multi-docker
5. Set Description to multi-docker
6. Set VPC to default VPC
7. Click Create Button
8. Click Close
9. Manually tick the empty field in the Name column of the new security group and type multi-docker, then click the checkmark icon.
10. Scroll down and click Inbound Rules
11. Click Edit Rules button
12. Click Add Rule
13. Set Port Range to 5432-6379
14. Click in box next to Custom and start typing 'sg' into the box. Select the Security Group you just created, it should look similar to 'sg-…. | multi-docker’
15. Click Save Rules button
16. Click Close

**Applying Security Groups to ElastiCache**

1. Go to AWS Management Console and use Find Services to search for ElastiCache
2. Click Redis in Sidebar
3. Check box next to Redis cluster and click Modify
4. Change VPC Security group to the multi-docker group and click Save
5. Click Modify

**Applying Security Groups to RDS**

1. Go to AWS Management Console and use Find Services to search for RDS
2. Click Databases in Sidebar and check box next to your instance
3. Click Modify button
4. Scroll down to Network and Security change Security group to multi-docker
5. Scroll down and click Continue button
6. Click Modify DB instance button

**Applying Security Groups to Elastic Beanstalk**

1. Go to AWS Management Console and use Find Services to search for Elastic Beanstalk
2. Click the multi-docker application tile
3. Click Configuration link in Sidebar
4. Click Modify in Instances card
5. Scroll down to EC2 Security Groups and tick box next to multi-docker
6. Click Apply and Click Confirm

**Setting Environment Variables**

1. Go to AWS Management Console and use Find Services to search for Elastic Beanstalk
2. Click the multi-docker application tile
3. Click Configuration link in Sidebar
4. Select Modify in the Software tile
5. Scroll down to Environment properties
6. In another tab Open up ElastiCache, click Redis and check the box next to your cluster. Find the Primary Endpoint and copy that value but omit the :6379
7. Set REDIS_HOST key to the primary endpoint listed above, remember to omit :6379
8. Set REDIS_PORT to 6379
9. Set PGUSER to postgres
10. Set PGPASSWORD to postgrespassword
11. In another tab, open up RDS dashboard, click databases in sidebar, click your instance and scroll to Connectivity and Security. Copy the endpoint.
12. Set the PGHOST key to the endpoint value listed above.
13. Set PGDATABASE to fibvalues
14. Set PGPORT to 5432
15. Click Apply button

**IAM Keys for Deployment**

1. Go to AWS Management Console and use Find Services to search for IAM
2. Click Users link in the Sidebar
3. Click Add User button
4. Set User name to multi-docker-deployer
5. Set Access-type to Programmatic Access
6. Click Next:Permissions button
7. Select Attach existing polices directly button
8. Search for 'beanstalk' and check all boxes
9. Click Next:Review
10. Add tag if you want and Click Next:Review
11. Click Create User
12. Copy Access key ID and secret access key for use later

**AWS Keys in Travis**

1. Open up Travis dashboard and find your multi-docker app
2. Click More Options, and select Settings
3. Scroll to Environment Variables
4. Add AWS_ACCESS_KEY and set to your AWS access key
5. Add AWS_SECRET_KEY and set to your AWS secret key



Modify travis yml

New **.travis.yml**

```yaml
sudo: required
services:
  - docker

before_install:
  - docker build -t adysingh1989/react-test -f ./client/Dockerfile.dev ./client

script:
  - docker run -e CI=true adysingh1989/react-test npm test -- --coverage

after_success:
  - docker build -t adysingh1989/multi-client ./client
  - docker build -t adysingh1989/multi-nginx ./nginx
  - docker build -t adysingh1989/multi-server ./server
  - docker build -t adysingh1989/multi-worker ./worker
  - echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_ID" --password-stdin
  - docker push adysingh1989/multi-client
  - docker push adysingh1989/multi-nginx
  - docker push adysingh1989/multi-server
  - docker push adysingh1989/multi-worker

#Change this stuff
deploy:
  provider: elasticbeanstalk
  region: "us-east-2"
  app: "docker-react"
  env: "DockerReact-env"
  bucket_name: "elasticbeanstalk-us-east-2-509296601184"
  bucket_path: "docker-react"
  on:
    branch: master
  access_key_id: $AWS_ACCESS_KEY
  secret_access_key: 
    secure: "$AWS_SECRET_KEY"
```

## Setting Up Kubernetes Development Environment

This will start a kubenetes node on macbook -

```
brew install kubectl
which kubectl
//Install virtualbox
brew cask install minikube
which minikube
minikube start
```

**Docker desktop kubernetes**

#### **macOS**

1. Click the Docker icon in the top macOS toolbar

2. Click Preferences

3. Click "Kubernetes" in the dialog box menu

4. Check the “Enable Kubernetes” box

5. Click "Apply"

6. Click Install to allow the cluster installation (This may take a while).

#### **Usage**

Going forward, any minikube commands run in the lecture videos can be ignored. Also, instead of the IP address used in the video lectures when using minikube, we use localhost.

For example, in the first project where we deploy our simple React app, using minikube we would visit:

192.168.99.101:31515

Instead, when using Docker Desktop's Kubernetes, we would visit: **localhost:31515**

Also, you can skim through the discussion about needing to use the local Docker node in the "Multiple Docker Installations" and "Why Mess with Docker in the Node" lectures (187-189), this only applies to minikube users.

```
MacBooks-MacBook-Pro:TechNotebooks macbookpro$ minikube status
host: Stopped
kubelet: 
apiserver: 
kubectl: 
MacBooks-MacBook-Pro:TechNotebooks macbookpro$ kubectl cluster-info
Kubernetes master is running at https://kubernetes.docker.internal:6443
KubeDNS is running at https://kubernetes.docker.internal:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
MacBooks-MacBook-Pro:TechNotebooks macbookpro$ 

```

```
mkdir simplek8s
```

Client-pod.yml

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: client-pod
  labels:
    component: web
spec:
  containers:
    - name: client
      image: adysingh1989/multi-client
      ports:
        - containerPort: 3000
```

Client-node-port.yml

```yaml
apiVersion: v1
kind: Service
metadata:
  name: client-node-port
spec:
  type: NodePort
  ports:
    - port: 3050
      targetPort: 3000
      nodePort: 31515
  selector:
    component: web
```

```
MacBooks-MacBook-Pro:simplek8s macbookpro$ kubectl apply -f ./client-pod.yaml
pod/client-pod unchanged
MacBooks-MacBook-Pro:simplek8s macbookpro$ kubectl apply -f client-node-port.yaml 
service/client-node-port unchanged
MacBooks-MacBook-Pro:simplek8s macbookpro$ kubectl get pods
NAME         READY   STATUS             RESTARTS   AGE
client-pod   0/1     CrashLoopBackOff   4          3m2s
MacBooks-MacBook-Pro:simplek8s macbookpro$ 

kubectl get services
minikube start
minikube ip
kubectl get pods
kubectl get <objecttype>
kubectl describe pod client-pod
kubectl delete -f <configfile>
```

client-deployment.yaml

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: client-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      component: web
  template:
    metadata:
      labels:
        component: web
    spec:
      containers:
        - name: client
          image: adysingh1989/multi-client
          ports:
            - containerPort: 3000
```

```
kubectl apply -f <objectfile>
kubectl get deployments
kubectl get pods -o wide
```

changing image

```
kubectl set image <objecttype> / <objectname> <containername> = <newimage>
```

```
eval $(minikube docker-env) 
kubectl podname logs
kubectl exec -it podname sh
kubectl delete deployment <name>
```

