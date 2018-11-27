# BeepBeep-composer

Make sure to have docker-compose installed 
```
$ docker-compose --version
```
cd to this directory and simply run
```
$ docker-compose up
```

sit down, relax and watch those beautiful lines on your terminal.

When the build has finished every microservice is up, connected and running, you can access them from browser or postman or whatever


If you need to rebuild everything just run

```
$ docker-compose build
```

If you want to rebuild specific microservice

```
$ docker-compose build dataservice
```

If you need to change where the docker-compose takes the source files just change the address in the `docker-compose.yml`

## Useful scripts

Docker is fun but it creates a lot of garbage so runs this command to remove everything you have created

1) Remove Containers: Not very much space reclaimed but you also don't lose much
	* A container is created from an image, `docker-compose up` use the same created containers instead `docker run` creates a new container each time you use it
	```
	$ docker container rm $(docker ps -aq)
	```
2) Remove Images: Images occupy a lot of space mostly because of the images of python.
	* Removing all the images comports that `docker-compose up` has to download and create again every image from scratch
	```
	$ docker rmi $(docker images -aq)
	```
3) Remove Volumes: Every image with a database use a volume for persistance, it's not much but why not
	```
	$ docker volume rm $(docker volume ls -q)
	```
4) Remove Networks: The docker compose created use a shared network between the microservices let's remove also that
	```
	$ docker network rm $(docker network ls -q)
	```
