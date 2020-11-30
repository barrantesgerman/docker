 

# MySQL

## Docker

### Pull

```bash
$ docker pull mysql
```

### Run

Basic

```bash
$ docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=secret --name mysql-db mysql:tag
```

Config

```bash
$ docker run -d -p 3306:3306 -v /my/own/datadir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=secret -e MYSQL_DATABASE=mydb -e MYSQL_USER=user -e MYSQL_PASSWORD=pass --name mysql-db mysql:tag
```

### Use

Container

```bash
$ docker exec -it mysql-db mysql -p
```

External

```bash
$ docker run -it --rm mysql mysql -hsome-mysql-host -usome-mysql-user -p
```

## Docker Compose

### Examples

Adminer

```yaml
# Use root/example as user/password credentials
version: '3.1'

services:

  db:
    image: mysql
    command: --default-authentication-plugin=mysql_native_password
    environment:
      MYSQL_ROOT_PASSWORD: example

  adminer:
    image: adminer
    ports:
      - 8080:8080 
```

Spring Boot

```yaml
version: '3.7'
services:
  db:
    image: mysql:8.0
    ports:
      - "3306:3306"
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: example
      MYSQL_PASSWORD: example
      MYSQL_ROOT_PASSWORD: root
    networks:
      - backend
  app-server:
    build:
      context: . 
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    depends_on:
      - db
    environment:
      SPRING_DATASOURCE_URL: jdbc:mysql://db:3306/exampledb?useSSL=false&allowPublicKeyRetrieval=true
      SPRING_DATASOURCE_USERNAME: example
      SPRING_DATASOURCE_PASSWORD: example
    networks:
      - backend
    command: ["java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/SpringBoot.jar"]
networks:
  backend:
```


## Links

https://hub.docker.com/_/mysql

https://platzi.com/tutoriales/1432-docker/3268-como-crear-un-contenedor-con-docker-mysql-y-persistir-la-informacion/