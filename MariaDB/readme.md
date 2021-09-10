# MariaDB

## Docker

### Pull

```shell
$ docker pull mariadb
```

### Run

Basic

```shell
$ docker run -d -p 3306:3306 -e MARIADB_ROOT_PASSWORD=secret --name maria-db maria:tag
```

Config

```shell
$ docker run -d -p 3306:3306 -v /my/own/datadir:/var/lib/mysql -e MARIADB_ROOT_PASSWORD=secret -e MARIADB_DATABASE=mydb -e MARIADB_USER=user -e MARIADB_PASSWORD=pass --name maria-db mariadb:tag
```

### Use

Container

```shell
$ docker exec -it --rm maria-db mysql -p
```

External

```shell
$ docker run -it --rm maria-db mysql -hsome-mariadb-host -usome-mariadb-user -p
```

## Docker Compose

### Examples

Adminer

```yaml
# Use root/example as user/password credentials
version: '3.1'

services:

  db:
    image: mariadb
    command: --default-authentication-plugin=mysql_native_password
    environment:
      MARIADB_ROOT_PASSWORD: example

  adminer:
    image: adminer
    ports:
      - 8080:8080 
```

## Links

* [MariaDB Docker](https://hub.docker.com/_/mariadb/)