# Asciidoctor

## Docker

### Pull

```shell
$ docker pull asciidoctor/docker-asciidoctor
```

### Run

Basic

```shell
$ docker run --rm -it -v /path/to/document:/data asciidoctor/docker-asciidoctor
```

To run Asciidoctor on a basic AsciiDoc file

```shell
$ asciidoctor sample.adoc
$ asciidoctor-pdf sample.adoc
$ asciidoctor-epub3 sample.adoc
```

To run AsciiDoc on an AsciiDoc file that contains diagrams

```shell
$ asciidoctor -r asciidoctor-diagram sample-with-diagram.adoc
$ asciidoctor-pdf -r asciidoctor-diagram sample-with-diagram.adoc
$ asciidoctor-epub3 -r asciidoctor-diagram sample-with-diagram.adoc
```

To use Asciidoctor Confluence

```shell
$ asciidoctor-confluence --host HOSTNAME --spaceKey SPACEKEY --title TITLE --username USER --password PASSWORD sample.adoc
```

To use Asciidoctor reveal.js with local downloaded reveal.js

```shell
$ asciidoctor-revealjs sample-slides.adoc
$ asciidoctor-revealjs -r asciidoctor-diagram sample-slides.adoc
```

To use Asciidoctor reveal.js with online reveal.js

```shell
$ asciidoctor-revealjs -a revealjsdir=https://cdnjs.cloudflare.com/ajax/libs/reveal.js/3.9.2 sample-slides.adoc
$ asciidoctor-revealjs -a revealjsdir=https://cdnjs.cloudflare.com/ajax/libs/reveal.js/3.9.2 -r asciidoctor-diagram sample-slides.adoc
```

### Example ADOC File

sample.adoc

```
= Document Title
Doc Writer <doc@example.com>
:doctype: book
:reproducible:
//:source-highlighter: coderay
:source-highlighter: rouge
:listing-caption: Listing
// Uncomment next line to set page size (default is A4)
//:pdf-page-size: Letter

A simple http://asciidoc.org[AsciiDoc] document.

== Introduction

A paragraph followed by a simple list with square bullets.

[square]
* item 1
* item 2

Here's how you say "`Hello, World!`" in Prawn:

.Create a basic PDF document using Prawn
[source,ruby]
----
require 'prawn'

Prawn::Document.generate 'example.pdf' do
  text 'Hello, World!'
end
----

== Mathematics

Even asciidoctor-mathematical is supported:

:stem: latexmath

[stem]
++++
sqrt(4) = 2
++++
```

## Links

* [Asciidoctor Docker](https://hub.docker.com/r/asciidoctor/docker-asciidoctor)
* [Github](https://github.com/asciidoctor/docker-asciidoctor)
* [Asciidoctor](https://asciidoctor.org/)