 

# Mermaid-Server

## Docker

### Pull

```shell
$ docker pull tomwright/mermaid-server
```

### Run

Basic

```shell
$ docker run -d --name mermaid-server -p 80:80 tomwright/mermaid-server
```

### cURL

Use the query param 'type' to change between 'png' and 'svg' defaults to 'svg'.

**POST**

```shell
$ curl --location --request POST 'http://localhost:80/generate' \
--header 'Content-Type: text/plain' \
--data-raw 'graph LR
    A-->B
    B-->C
    C-->D
    C-->F
'
```

**GET**

```shell
$ curl --location --request GET 'http://localhost:80/generate?data=graph%20LR%0A%0A%20%20%20%20A--%3EB%0A%20%20%20%20B--%3EC%0A%20%20%20%20C--%3ED%0A%20%20%20%20C--%3EF%0A'

```

### Caching

All generated diagram input and output will be cached for 1 hour. The cache time is reset whenever a cached diagram is accessed.

## Links

* [Mermaid-Server Docker](https://hub.docker.com/r/tomwright/mermaid-server)
* [Github](https://github.com/TomWright/mermaid-server)
* [Mermaid JS](https://mermaid-js.github.io/mermaid/#/)