# Tools

# dbt

1. Video Tutorial

[dbt (data build tool) Crash Course For Beginners (dbt Core) | Full Tutorial](https://www.youtube.com/watch?v=toSAAgLUHuk)

1. dbt sample project: [https://github.com/harsh1kumar/learning/tree/master/dbt](https://github.com/harsh1kumar/learning/tree/master/dbt)

# Docker

### Install

If not possible to install docker-desktop due to licence requirements, use `colima` ([details](https://github.com/abiosoft/colima))

### Commands

- docker run nginx
- docker run -p 8080:80 nginx `map 8080 port to port 80 of nginx container`
- docker ps
- docker ps -a
- docker run -d nginx  `starts nginx docker container in background`
- docker stop <first few letters of Container ID>
- docker rm <container ID>
- docker rm -f <container ID>/name `delete a running container forcefully`
- docker start <container ID>/name
- docker images
- docker system prune

- docker cp this.png <first few letters of Container ID>:th.txt
- docker exec -it <first few letters of Container ID> bash
- docker run -it <docker-image> bash
    - docker run -it <docker-image> /bin/sh —login `for alpine images`
- docker cp <first few letters of Container ID>:mine.txt this.uu // copy from container to source
- docker exec -it <Container_ID> bash // executes a command inside an existing container
- docker commit container

> **How is `docker run` different from `docker exec`?**
`docker run` is the command you use to create a new container from an image, whilst `docker exec` lets you run commands on an already running container
> 

**Docker cheat sheet**: [https://dockerlabs.collabnix.com/docker/cheatsheet/](https://dockerlabs.collabnix.com/docker/cheatsheet/)

### Sample Dockerfile

```docker
FROM python:3.7-alpine

COPY . /app
WORKDIR /app
ENV MY_ENV=some_value

RUN pip install -r requirements.txt
EXPOSE 5000  # Expose port 5000 from container to host machine

CMD python app.py
```

> **How is `RUN` different from `CMD`?**

1. `RUN` gets executed during docker build and creates another layer in the image. `CMD` executes when the docker file in run.
2. Multiple `RUN` can be executed in dockerfile, but only the last `CMD` is executed
> 

- docker build .
- docker build -t vieux/apache:latest -t vieux/apache:2.0

### Docker Compose

- docker compose up
- docker compose stop

Sample `docker-compose.yml` file

```yaml
version: '3'
services:
  app:
    image: my-app
		build: .
    ports:
      - "8000:8000"
    working_dir: /app
    environment:
      MYAPP_ENV: some_env
  mongo:
    image: mongo
    container_name: app_mongo
    restart: always
```

### Videos

1. Short Tutorial by Harry

[Ultimate Docker Crash Course: Learn Docker within 30 Minutes!](https://www.youtube.com/watch?v=WNUCAPKa44Y)

1. Full Tutorial

[Complete Dockers For Data Science Tutorial In One Shot](https://www.youtube.com/watch?v=8vmKtS8W7IQ)