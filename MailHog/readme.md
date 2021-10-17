# MailHog

## Docker

### Pull

```shell
$ docker pull mailhog/mailhog
```

### Run

Basic

```shell
$ docker run -d --name mailhog -p 1025:1025 -p 8025:8025 mailhog/mailhog
```

Config

```shell
$ docker run -d --name mailhog -e MH_STORAGE:maildir -e MH_MAILDIR_PATH:/maildir -v $PWD/maildir:/maildir -p 1025:1025 -p 8025:8025 mailhog/mailhog
```

[Configuring MailHog](https://github.com/mailhog/MailHog/blob/master/docs/CONFIG.md)

### Open

[Main Page](http://localhost:8025/)

## Java Mail Configuration Example

```properties
mail.smtp.host=localhost
mail.smtp.port=1025
mail.smtp.from=test@mail.com
mail.debug=true
mail.smtp.timeout=10000
mail.smtp.connectiontimeout=10000
mail.smtp.writetimeout=10000
```

## Links

* [MailHog Docker](https://hub.docker.com/r/mailhog/mailhog)
* [MailHog Github](https://github.com/mailhog/MailHog)