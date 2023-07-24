# Hello, World!

This is an example of how to quickly serve an Apache server
through a docker container.

## The necessary files

For this example, we'll be using the following file
structure:

```text
./
├── compose.yaml
├── public-html/
│   └── index.html
├── readme.md
└── template.html
```

with the contents of `compose.yaml` as follows

```YAML
version: '3.9'
services:
  apache:
    image: httpd:latest
    container_name: my-apache-app
    ports:
      - '80:80'
    volumes:
      - ./public-html:/usr/local/apache2/htdocs
```

Note that the `template.html` file was used with `pandoc` to
generate the `public-html/index.html` page.

## Starting the server

To start serving, first, `cd` to the same level as the
`compose.yaml` file and then run

```bash
docker compose up -d
```

Assuming everything is working fine, your container should
be up and visible if running

```bash
docker container ls
```

To check the served page, open an internet browser and type
the ip of the machine running the docker container, under
the default port `80`. If you installed `ip`, check the
machine's ip with

```bash
ip -br addr
```

Hopefully, if everything went *just right*, you should be
seeing this documentation on your browser.
