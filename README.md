# HTML Proofer, Dockerized

HTML validation, made easy. This repository is the [HTML Proofer](https://github.com/gjtorikian/html-proofer) Ruby gem wrapped up in a Docker container, so you don't have to fuss with installing things like [Ruby](https://www.ruby-lang.org/) or [Nokogiri](http://www.nokogiri.org/).

## Usage

Requires [Docker](https://www.docker.com/).

```bash
docker run moss/html-proofer
```

This will print out the usage instructions. Arguments for [the `htmlproofer` CLI](https://github.com/gjtorikian/html-proofer#using-on-the-command-line) can then be appended to the command. Note that **it's not (yet) recommended this be used against live sites** due to [this issue](https://github.com/gjtorikian/html-proofer/issues/334).

### Single file

You will need to [mount the file as a data volume](https://docs.docker.com/engine/userguide/containers/dockervolumes/#mount-a-host-file-as-a-data-volume) so it's available in the container, like so:

```bash
docker run -v /absolute/path/to/file.html:/file.html moss/html-proofer /file.html
```

### Directory of files

e.g. those created by a static site builder like [Jekyll](http://jekyllrb.com/) or [Hugo](https://gohugo.io/). You will need to [mount the directory as a data volume](https://docs.docker.com/engine/userguide/containers/dockervolumes/#mount-a-host-directory-as-a-data-volume) so it's available in the container, like so:

```bash
docker run -v /absolute/path/to/dir/:/site moss/html-proofer /site
```
