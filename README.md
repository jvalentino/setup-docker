# Docker Setup

The purpose of this project is to explain how to install both Docker and Docker Compose, while then providing a basic example on how to use them.

What is Docker? A way to run an operating system, without another operating sytem.

> Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. The service has both free and premium tiers. The software that hosts the containers is called Docker Engine. It was first started in 2013 and is developed by Docker, Inc

- https://en.wikipedia.org/wiki/Docker_(software)

What is Docker Compose? A way to configure Docker using a YAML file instead of all those different commands.

> Docker Compose is **a tool for running multi-container applications on Docker defined using the Compose file format**. A Compose file is used to define how the one or more containers that make up your application are configured.

- https://github.com/docker/compose

# Docker Desktop

Docker Desktop contains both the docker command-line, and a nifty graphical user interfaces for managing containers and running various commands for you.

Reference: https://www.docker.com/products/docker-desktop/

However, you need to be vary careful about how you use it, to so some major licensing changes:

> - It **remains free** for small businesses (fewer than 250 employees AND less than $10 million in annual revenue), personal use, education, and non-commercial open source projects.
> - It requires a paid subscription ([Pro, Team or Business](https://www.docker.com/pricing/)), for as little as $5 per user per month, for professional use in larger businesses.
> - The effective date of these terms is August 31, 2021. **There is a grace period until January 31, 2022** for those that will require a paid subscription to use Docker Desktop.
> - The Docker Pro, Docker Team, and Docker Business subscriptions **now include** commercial use of Docker Desktop.
> - Check out our [FAQ](https://www.docker.com/pricing/faq/) for more information. Or read our [latest blog](https://www.docker.com/blog/updating-product-subscriptions/).

Essentially, if you are a business maing more than $10 million a year, you need to pay to use this.

## Docker Desktop Alternative Installation

If you are on Mac, you can use [Homebrew](https://brew.sh/) to install Docker Desktop:

```bash
$ brew install --cask docker
```

# Docker Desktop Alternative

Get familiar with Docker Command-line, because you are going to need it: https://dockerlabs.collabnix.com/docker/cheatsheet/

![](https://raw.githubusercontent.com/sangam14/dockercheatsheets/master/dockercheatsheet8.png)

Actually getting docker without the desktop can also be complicated depending on your operating system.

## Mac

If you are on Mac, you can use [Homebrew](https://brew.sh/) to install Docker without the Desktop:

```bash
$ brew install docker
```

## WIndows

Sorry, but this is going to be very difficult: https://dev.to/_nicolas_louis_/how-to-run-docker-on-windows-without-docker-desktop-hik

The way figured out was to install the Docker plugin via Visual Studio Code, and then configure it to be accessible via the command-line.

## Linux

Thankfully not as complicated as Windows: https://docs.docker.com/engine/install/ubuntu/

It has you installing docker via apt-get:

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

# How do I know it worked?

Verify docker:

```bash
$ docker --version
Docker version 20.10.17, build 100c701
```

Verify docker compose:

```bash
$ docker compose version
Docker Compose version v2.7.0
```

Now it is time to run the demonstration application!

docker-compose.yml

```yaml
version: '3.8'
services:
    client:
        image: nginx
        container_name: nginx
        ports:
            - 8000:80
        volumes:
            - ./html:/usr/share/nginx/html
```

This is magic for running an nginx web server at http://localhost:8000, in which the content of ./html is the root of that web site. Because index.html is in that folder and the default filename for a webpage, it is what is displayed on that address.

You can startup that container (and leave it open, which means you have to Control + C) to kill it using:

```bash
$ docker compose up
```

![01](./wiki/01.png)



