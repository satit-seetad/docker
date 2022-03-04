# docker
How to use docker

## List container
`docker ps`<br>
`docker ps -a`      => show all containers

## Build image
`docker build .` => create docker image<br>
`docker build -f <docker_file> .`	=> create docker image with specific dockerfile<br>
`docker build -t <docker_id>/<name> .`  => create docker image with tag

## Create container
`docker create <image_id>` => create container

## Start container
`docker start <container_id>` => start container

## Run container (create + start)
`docker run <image_id>` => run container<br>
`docker run -p 3000:3000 <container_id>`    => run container with port mapping<br>
`docker run -v /app/node_modules -v ${pwd}:/app <container_id>`	=> run container with volume mapping<br>
`docker run -it <container_id> <command>`   => run container with command line

## Stop container
`docker stop <container_id>`<br>
`docker kill <container_id>`

## Clear image cache
`docker system prune -a`

## Push to docker hub
`docker login`<br>
`docker login -u "<username>" --password-stdin "<password>"`<br>
`docker push <image_id>`	=> push image to docker hub

## Docker compound
`docker-compose up`<br>
`docker-compose up --build`<br>
`docker-compose down`

## Dockerfile example
`FROM node:alpine`<br><br>

`WORKDIR '/app'`<br>
`COPY package.json .`<br><br>

`RUN npm install`<br><br>

`COPY . .`<br>

`CMD ["npm", "run", "start"]`

## Docker compose example
`version: '3'`<br>
`services:`<br>
&nbsp;&nbsp;&nbsp;`web:`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`build:`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;`context: .`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`dockerfile: Dockerfile.dev`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`ports:`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`- "3000:3000"`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`volumes:`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`- /app/node_modules`<br>
&nbsp;&nbsp;&nbsp;`tests:`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `command: ["npm", "run", "test"`



