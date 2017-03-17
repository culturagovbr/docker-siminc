# docker-siminc

Repo used to have a recipe(Dockerfile) to create a image used by siminc

### Prerequisites
* Docker - More information [here](http://pt.slideshare.net/vinnyfs89/docker-essa-baleia-vai-te-conquistar?qid=aed7b752-f313-4515-badd-f3bf811c8a35&v=&b=&from_search=1).

### Steps
* Build image
* Clone siminc project from [here](http://git.cultura.gov.br/sistemas/siminc)
* Create a container from image created
* Copy files 'config.inc' and 'database.php' to './includes/global'

### Folder structure to create container
```
 .. # docker-siminc folder
 .
 \siminc # cloned project
 \ZendFramework # lib dependencies
```

### How to build - New image
* Enter inside this cloned repository;
* Execute the commando below to create a new image.
```
docker build -t siminc:1.0 .
```

This code `-t siminc:1.0` means you will create a image named 'siminc' and tag '1.0' and the `.` means your build will use the same folder.

You can execute the command below to create a new container using this new image created. Note: `$(pwd)` means your current directory. You can also change it, if you want.
```
docker run -it -v $(pwd):/var/www --name simincv1.0 -e APPLICATION_ENV="development" -p 80:80 -p 9000:9000 siminc:1.0&
```

Or You you can also execute the same command above, but arranging using docker-compose:
```
@todo fill here
```

### Extra

If you wanna check something inside your container you can access using the command below:
```
docker exec -it simincv1.0 bash
```

See the authors of this repo:
* [Authors](./Authors.md).
