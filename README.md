# Run container
* create container
```docker create [image_id]```

* run container
```docker start [container]```

* download image and run container
```docker run [image]```

* run with command
```docker run [image] [command]```

* execute container
```docker exec [container] [command]```
```docker run -it [image] [command]```
```docker run -d [image]```  // run in background

* port mapping
```docker run -p [ext.port][int.port] [image]```

* volume mapping
```docker run -v [ex.dir][int.dir] [image]```

* name setting
```docker run --name=[name] [image]```

* environment variable
```docker run -e [env]=[value] [image]```

* override entrypoint
```docker run --entrypoint [cmd] [image]```

* link with other container
```docker run --link [name to call]:[name container] [image]```

* network
```docker run [image]``` // use bridge network
```docker run [image] --network=none```   // no network
```docker run [image] --network=host```  // use host network

* resource limit
```docker run --cpus=.5 [image]```
```docker run --memory=100m [image]```

# Manage/check container

* list running containers
```docker ps```

* list all containers
```docker ps -a```

* stop container
```docker stop [container]```

* remove container
```docker rm [container]...```

* kill container
```docker kill [container]```

* attach container
```docker attach [container]```

* inspect container
```docker inspect [container]```

* check log from container
```docker logs [container]```


# Image

* list image
```docker images```

* delete imgage
```docker rmi [image]```

* pull image
```docker pull [image]```

* build image
```docker build .```
```docker build . -t [tag]```  
```docker build -f [docker_file]```  

* push image
```docker login```
```docker login -u "[username]" --password-stdin "[password]"```
```docker push [account]/[name]```

# System
* check size usage of docker
```docker system df```

* show all images with size
```docker system df -v```

* delete all files
```docker system prune -a```

# Network
* create network
```docker network create --driver bridge subnet [subnet][network_name]```
	
* list all networks
```docker network ls``` 

# Volume

```docker volume create [volume_name]``` // created under /var/lib/docker/volumes folder
```docker run -v [volume_name]:[volume_container] [image]```
```docker run -v [path_host]:[path_container] [image]```

# Private registry
```docker run -d -p 5000:5000 --name registry registry:2```
```docker image -t my_image localhost:5000/my_image```
```docker push localhost:5000/my_image```
```docker pull localhost:5000/my_image```

# Other
* check version
```docker version```
* docker engine
```docker -H=[host:port] run [image]```


* cmd vs entrypoint
 ```CMD sleep 5``` => docker run xxx sleep 10 => will replace
```ENTRYPOINT ["sleep"]``` => docker run xxx 10 => will append to the sleep as parameter
```ENTRYPOINT ["sleep"]  CMD ["5"]``` => docker run xxx => will run default and also put the parameter

# Docker Compose
* start
```docker-compose up```
```docker-compose up --build```

* stop
```docker-compose down```


* structure
```
version: 2
services:
	[name]:
		image:
		ports:
			-[port]:[port]
		links	=> use for v1 only
			-[name container]
		depends_on:
			-[name container]
		build: [path of dockerfile]
		networks:
			-[network]
		environment:
			[name]: [value]
networks:
	[network1]:
	[network2]
```
