# Jekyll

## Docker

### Pull

```shell
$ docker pull jekyll/jekyll:3.8
```

### Run

Create a new Jekyll site at `./blog`

```shell
$ docker run --rm -v $PWD:/srv/jekyll -it jekyll/jekyll:3.8 jekyll new blog
```

Change into your new directory

```shell
$ cd blog
```

Build the site

```shell
$ docker run --rm -v $PWD:/srv/jekyll -it jekyll/jekyll:3.8 jekyll build
```

Make it available on a local server

```shell
$ docker run --rm -v $PWD:/srv/jekyll -p 4000:4000 -it jekyll/jekyll:3.8 jekyll serve
```

Pass the `--livereload` option to `serve` to automatically refresh the page with each change you make to the source files

```shell
$ docker run --rm \
	-v $PWD:/srv/jekyll \
	-p 4000:4000 \
	-it jekyll/jekyll:3.8 \
	jekyll serve --livereload
```

### Open

[Main Page](http://localhost:4000/)

## Links

* [Jekyll Site](https://jekyllrb.com/)
* [Jekyll Docker Site](https://github.com/envygeeks/jekyll-docker/blob/master/README.md)