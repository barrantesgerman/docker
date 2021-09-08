 

# Mermaid-CLI

## Docker

### Pull

```bash
$ docker pull minlag/mermaid-cli
```

### Run

Basic

```bash
$ docker run --rm -it -v /path/to/diagrams:/data minlag/mermaid-cli -i /data/diagram.mmd
```

SVG

```bash
$ docker run --rm -it -v /path/to/diagrams:/data minlag/mermaid-cli -i /data/diagram.mmd -o /data/diagram.svg
```

PDF

```bash
$ docker run --rm -it -v /path/to/diagrams:/data minlag/mermaid-cli -i /data/diagram.mmd -o /data/diagram.pdf
```

PNG

```bash
$ docker run --rm -it -v /path/to/diagrams:/data minlag/mermaid-cli -i /data/diagram.mmd -o /data/diagram.png -t dark -b transparent
```

### CLI Arguments

| Argument                                         | Description                                                  |
| ------------------------------------------------ | ------------------------------------------------------------ |
| `-t, --theme [theme]`                            | Theme of the chart, could be default, forest, dark or neutral. Optional. Default: default |
| `-w, --width [width]`                            | Width of the page. Optional. Default: 800                    |
| `-H, --height [height]`                          | Height of the page. Optional. Default: 600                   |
| `-i, --input <input>`                            | Input mermaid file. Required.                                |
| `-o, --output [output]`                          | Output file. It should be either svg, png or pdf. Optional. Default: input + ".svg" |
| `-b, --backgroundColor [backgroundColor]`        | Background color. Example: transparent, red, \'#F0F0F0\'. Optional. Default: white |
| `-c, --configFile [configFile]`                  | JSON configuration file for mermaid. Optional                |
| `-C, --cssFile [cssFile]`                        | CSS file for the page. Optional                              |
| `-s, --scale [scale]`                            | Puppeteer scale factor, default 1. Optional                  |
| `-f, --pdfFit [pdfFit]`                          | Scale PDF to fit chart                                       |
| `-p --puppeteerConfigFile [puppeteerConfigFile]` | JSON configuration file for puppeteer. Optional              |

### Example MMD File

diagram.mmd

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

## Links

* [Mermaid-CLI Docker](https://hub.docker.com/r/minlag/mermaid-cli)
* [Github](https://github.com/mermaid-js/mermaid-cli)
* [Mermaid JS](https://mermaid-js.github.io/mermaid/#/)