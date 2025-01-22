---
title: "Database setup with podman/ Docker containers"
date: 2025-01-22T19:18:35+06:00
lastmod: 2025-01-22T19:18:35+06:00
draft: true
author: "Sharafat Karim"
authorLink: "https://sharafat.pages.dev/about/"
description: "An Quickstart guide for starting your journey with database alongside a bit of containers, especially for Linux guys!"
license: ""
images: []
resources:
- name: "featured-image"
  src: "featured-image.jpg"
- name: "featured-image-preview"
  src: "featured-image.jpg"

tags: ["software", "basic", "linux", "arch"]
categories: ["tutorial"]
summary: "An Quickstart guide for starting your journey with database alongside a bit of containers, especially for Linux guys!"

featuredImage: "featured-image"
featuredImagePreview: "featured-image-preview"

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: false

toc:
  enable: true
  auto: true
code:
  copy: true
  maxShownLines: 50
math:
  enable: false
  # ...
mapbox:
  # ...
share:
  enable: true
  # ...
comment:
  enable: true
  # ...
library:
  css:
    # someCSS = "some.css"
    # located in "assets/"
    # Or
    # someCSS = "https://cdn.example.com/some.css"
  js:
    # someJS = "some.js"
    # located in "assets/"
    # Or
    # someJS = "https://cdn.example.com/some.js"
seo:
  images: []
  # ...
license: '<a rel="license external nofollow noopener noreffer" href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">CC BY-NC 4.0</a>'
---

## My SQL

MySQL is a RDBMS software which use SQL like syntax to manage databases. Nowadays most of the major linux distributions come with maria db preinstalled, which is an open source drop in replace ment for MySQL. I’ll be writing about some ways to install MySQL in linux based operating systems,

## XAMPP

Xampp is a popular tool which is an open source cross-platform web server solution stack package developed by Apache friends. It can be installed via the official website’s installer. Here a `.run` file will be downloaded which can be installed by executing from a terminal. But it is not recommended to install in this way.
The most recommended way is to search for a similar package in distros native package manager. For example, in Arch Linux the package is available through AUR (Arch User Repository). Here’s the git-clone URL,

- <https://aur.archlinux.org/packages/xampp>

To install it, we can use a AUR wrapper like `yay`. To do so, use the following command to query and install the latest version of `xampp`.

```bash
yay xampp
```

After installing open the app, head over to the second tab and start database and web server. Web UI will be available under `localhost`.

## Podman Container

One another good way to install MySQL is to use a podman or docker container. I personally prefer podman so I will be writing about it. Installing a container running only MySQL is pretty much easy. We just have to grub the image and run it in a container. It’s volume will be created automatically. Or if we also want to include a phpmyadmin web app to manage our image then we actually have to use a pod to contain two different containers.

### MySQL image

To setting up MySQL image, we can pull it from dockerhub. The command will be like,

```bash
podman pull mysql
```

then, we can start and run our image with the following command,

```bash
podman run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=tree --name mysql-db mysql:latest
```

Here our root password is defined as tree by the environement variable `MYSQL_ROOT_PASSWORD`.
And if we try to do list running process we can execute,

```bash
podman ps
```

It will see our image up and running. Now let’s actually enter to our server!

```bash
podman exec -it mysql-db mysql -u root -p
```

Let’s run a command to verify,

```bash
show databases;
```

It’ll list all databases.
Now with `localhost:3306` you can access this database from mysql workbench or other clients.

### Phpmyadmin image

Phpmyadmin is a web UI for managing MySQL databases. Let’s pull it first,

```bash
podman pull phpmyadmin
```

Now if run this image we won’t be able to access another image (MySQL) because there’s no connection in between them. So we will be using podman pod. Let’s create a podman pod,

```bash
podman pod create --name mysql -p 8080:8080 3306:3306
```

If we have previously created an image as per this guide and that is up and running, try the follwing command to stop and delete,

```bash
podman stop mysql-db && podman rm mysql-db
```

Now let’s start our mysql server under this pod,

```bash
podman run -d -e MYSQL_ROOT_PASSWORD=tree --pod mysql --name mysql-db mysql:latest
```

And finally let’s open our phpmyadmin with this pod,

```bash
podman run --name phpmyadmin -e PMA_ARBITRARY=1 -d --pod mysql phpmyadmin

```

It will be availabe under port 8080, as like we defined earlier. So let’s head over to,

- <http://localhost:8080/>

Here, our,

```text
Server = localhost:3306
Username = root
Password = tree
This can be also done graphically with the help of `podman desktop`.
```

### Docker

- Pull the image from the docker hub

```bash
docker pull mysql
```

or, using podman?

```bash
podman pull docker.io/library/mysql
```

- Now, let’s create our first container from the mysql image. Here is the command we will use:

```bash
docker run --name test-mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=tree -d mysql
```

> run: creates a new container or starts an existing one
>
> --name CONTAINER_NAME: gives the container a name. The name should be readable and short. In our case, the name is test-mysql.
>
> -e ENV_VARIABLE=value: the -e tag creates an environment variable that will be accessible within the container. It is crucial to set MYSQL_ROOT_PASSWORD so that we can run SQL commands later from the container. Make sure to store your strong password somewhere safe (not your brain).
>
> -d: short for detached, the -d tag makes the container run in the background. If you remove this tag, the command will keep printing logs until the container stops.
>
> image_name: the final argument is the image name the container will be built from. In this case, our image is mysql.
>
> -p HOST_PORT:CONTAINER_PORT: the -p tag maps a port from the host machine to the container. In this case, we are mapping port 3306 from the host to the container. This is the default port for MySQL.
>

If the command returns a long string of gibberish (the container ID), it means the container has started. You can check its status with docker ps:

- To access the terminal inside your container, you can use the following command:

```bash
docker exec -it container_name bash
```

- And then to login to mysql:

```bash
mysql -u root -p
```

## Troubleshooting

- <https://stackoverflow.com/questions/41645309/mysql-error-access-denied-for-user-rootlocalhost>
