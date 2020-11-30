 

# SonaQube

## Docker

### Pull

```bash
$ docker pull sonarqube
```

### Run

Basic

```bash
$ docker run -d -p 9000:9000 --name sonarqube-name sonarqube:tag
```

Config

```bash
$ docker volume create --name sonarqube_data
$ docker volume create --name sonarqube_logs
$ docker volume create --name sonarqube_extensions
$ docker run -d -p 9000:9000 -v sonarqube_data:/opt/sonarqube/data -v sonarqube_logs:/opt/sonarqube/logs -v sonarqube_extensions:/opt/sonarqube/extensions -e SONAR_JDBC_URL="url" -e SONAR_JDBC_USERNAME=user -e SONAR_JDBC_PASSWORD=pass --name sonarqube-name sonarqube:tag
```

## Docker Compose

### Examples

SonarQube with Postgres

```yaml
version: "3"

services:
  sonarqube:
    image: sonarqube:8-community
    depends_on:
      - db
    environment:
      SONAR_JDBC_URL: jdbc:postgresql://db:5432/sonar
      SONAR_JDBC_USERNAME: sonar
      SONAR_JDBC_PASSWORD: sonar
    volumes:
      - sonarqube_data:/opt/sonarqube/data
      - sonarqube_extensions:/opt/sonarqube/extensions
      - sonarqube_logs:/opt/sonarqube/logs
      - sonarqube_temp:/opt/sonarqube/temp
    ports:
      - "9000:9000"
  db:
    image: postgres:12
    environment:
      POSTGRES_USER: sonar
      POSTGRES_PASSWORD: sonar
    volumes:
      - postgresql:/var/lib/postgresql
      - postgresql_data:/var/lib/postgresql/data

volumes:
  sonarqube_data:
  sonarqube_extensions:
  sonarqube_logs:
  sonarqube_temp:
  postgresql:
  postgresql_data:
```


## Links

https://hub.docker.com/_/sonarqube

https://docs.sonarqube.org/latest/setup/install-server/

https://github.com/docker/for-win/issues/5202