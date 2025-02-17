---
title: Database setup with podman/ Docker containers
date: 2025-01-22T19:18:35+06:00
lastmod: 2025-01-22T19:18:35+06:00
draft: false
author: Sharafat Karim
authorLink: https://sharafat.pages.dev/about/
description: A quick start guide for starting your journey with database alongside a bit of containers, especially for Linux guys!
license: <a rel="license external nofollow noopener noreffer" href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">CC BY-NC 4.0</a>
images: 
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image.jpg
tags:
  - software
  - basic
  - linux
  - arch
categories:
  - tutorial
summary: A quick start guide for starting your journey with database alongside a bit of containers, especially for Linux guys!
featuredImage: featured-image
featuredImagePreview: featured-image-preview
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
mapbox: 
share:
  enable: true
comment:
  enable: true
library:
  css: 
  js: 
seo:
  images: []
---

A quick start guide for starting your journey with database alongside a bit of containers, especially for Linux guys! Please refer to the table of contents for jumping to the part you need!

## My SQL

MySQL is a RDBMS software which use SQL like syntax to manage databases. Nowadays most of the major Linux distributions come with maria db preinstalled, which is an open source drop in replacement for MySQL. I’ll be writing about some ways to install MySQL in linux based operating systems,

### Container Installation

One another good way to install MySQL is to use a podman or docker container. I personally prefer podman so I will be writing about it. Installing a container running only MySQL is pretty much easy. We just have to grub the image and run it in a container. It’s volume will be created automatically. Or if we also want to include a phpmyadmin web app to manage our image then we actually have to use a pod to contain two different containers.

#### Setup a container

Whatever, let's install podman! You can follow the official documentation for this. I guess most of the major linux distributions have podman in their official repositories.

Like, for Arch Linux:

```bash
sudo pacman -S podman
```

#### MySQL image

To setting up MySQL image, we can pull it from dockerhub. The command will be like,

```bash
podman pull mysql
```

> As an alternative you can also use [mariadb](https://hub.docker.com/_/mariadb) image.

Then, we can start and run our image with the following command,

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

#### Phpmyadmin image [OPTIONAL]

Phpmyadmin is a web UI for managing MySQL databases. Let’s pull it first,

```bash
podman pull phpmyadmin
```

Now if run this image we won’t be able to access another image (MySQL) because there’s no connection in between them. So we will be using podman pod. Let’s create a podman pod,

```bash
podman pod create --name mysql -p 8080:8080 3306:3306
```


{{< admonition type=warning title="BTW," open=true >}}

If we have previously created an image as per this guide and that is up and running, try the following command to stop and delete,

```bash
podman stop mysql-db && podman rm mysql-db
```

{{< /admonition >}}


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


> Hope you can figure out the rest! With the same approach as above, it's easy to setup any database. But if your'e using `docker`, unlike me, then you may need `kubernate` for creating pods. (Linking multiple containers).

### XAMPP

Xampp is a popular tool which is an open source cross-platform web server solution stack package developed by Apache friends. It can be installed via the official website’s installer. Here a `.run` file will be downloaded which can be installed by executing from a terminal. But it is not recommended to install in this way.
The most recommended way is to search for a similar package in distros native package manager. For example, in Arch Linux the package is available through AUR (Arch User Repository). Here’s the git-clone URL,

- <https://aur.archlinux.org/packages/xampp>

To install it, we can use a AUR wrapper like `yay`. To do so, use the following command to query and install the latest version of `xampp`.

```bash
yay xampp
```

After installing open the app, head over to the second tab and start database and web server. Web UI will be available under `localhost:8080`.

> `XAMPP` may use maria-db instead of MySQL. But that should not be an issue, I guess.


## Oracle Database

### Intro

Mainly I will be focusing linux, but will work on mac as well, with some of it's commands tweaked.

> For windows? You can download the installer from the official website and follow the instructions.
>
> - <https://www.oracle.com/database/technologies/xe-downloads.html>


### Container Installation

Docker and podman are the two most popular containerization tools. I will be using podman for this, and I will recommend podman as well. Why? Maybe I will write a blog on this later.

#### Setup a container

Whatever, let's install podman! You can follow the official documentation for this. I guess most of the major linux distributions have podman in their official repositories.

Like, for Arch Linux:

```bash
sudo pacman -S podman
```

#### Pull the image

There are mainly two images available for free, full and lite.

To get the full image:

```bash
podman pull container-registry.oracle.com/database/free:latest
```

And to be honest, it's a huge image around 9.48 G. So, I will recommend the lite version. It may take upto 2 G.

```bash
podman pull container-registry.oracle.com/database/free:23.5.0.0-lite
```

#### Run the container

Now let's go ahead and actually run the container.

```bash
podman run -d -p 1521:1521 --name oracle-db container-registry.oracle.com/database/free:23.5.0.0-lite
```

Here, I have used the lite version of the image. You can use the full version as well. Just replace the image name.
And the port `1521` is the default port for Oracle Database. You can change it if you want.

> Flag `-d` is used to run the container in the background.

> Flag `-p` is used to map the host port to the container port.

> Flag `--name` is used to give a name to the container. (Try to remember it!)

#### Set a password

Here I have used `1234` as the password. You can use whatever you want.

```bash
podman exec -it oracle-db ./setPassword.sh 1234
```

#### Connect to the database

You can use any database client to connect to the database. I will be using SQL\*Plus.

```bash
podman exec -it oracle-db sqlplus
```

And then enter the following details:

- Username: `system`
- Password: `1234` (Or the one you set in the previous step!)

#### Stop the container

```bash
podman stop oracle-db
```

#### Start the container

```bash
podman start oracle-db
```

> You may need to start the container if you have restarted your system!

### Vscode integration

It would be weird if we have to use terminal everytime we want to access our database, right?
Let's use vscode. Simply install the following extension,

- <https://marketplace.visualstudio.com/items?itemName=Oracle.sql-developer>

> Or, Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.
> 
> `ext install Oracle.sql-developer`.
> 
> The size of this extension is more than 300 M, so it'll take a bit of time.

- Now on our left/ right toolbar, you will find a icon, and maybe try to add a new connection? You will asked to fill up a form.

- For the port number try to use the one you got from `podman port oracle-db`.

- For the username, use `system`.

- And for the password, use the one you set in the previous steps.

- For the service name, it should be `FREE`. Or you can use the following code in `sqlplus` to get the service name,

```sql
SELECT VALUE 
FROM V$PARAMETER 
WHERE NAME = 'service_names';
```

And you are good to go!

## SQL server

For Microsoft SQL Server, you can do the same with above steps. Official docs are available here. Let's take a look,

- [Docker: Install Containers for SQL Server on Linux - SQL Server | Microsoft Learn](https://learn.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-ver16)
- [Deploy and Connect to SQL Server Linux Containers - SQL Server | Microsoft Learn](https://learn.microsoft.com/en-us/sql/linux/sql-server-linux-docker-container-deployment?view=sql-server-ver16&pivots=cs1-bash) 

### Container Installation

#### Setup a container

Whatever, let's install podman! You can follow the official documentation for this. I guess most of the major linux distributions have podman in their official repositories.

Like, for Arch Linux:

```bash
sudo pacman -S podman
```

#### Pull the image
Let's pull the image first,

```bash
podman pull mcr.microsoft.com/mssql/server:2022-latest
```


## Misc

### Port address

To get your outgoing forwarded port from podman, use the following,

```bash
podman port oracle-db     
```

### Listing all images

To list all of your podman images for space consumption, you can try,

```bash
podman images
```

Here's an example output,

```
REPOSITORY                                   TAG               IMAGE ID      CREATED        SIZE  
mcr.microsoft.com/mssql/server               2022-latest       b823451808db  12 days ago    1.63 GB  
docker.io/library/mysql                      latest            56a8c14e1404  3 months ago   621 MB  
container-registry.oracle.com/database/free  23.5.0.0-lite     742f1b37af1d  5 months ago   1.84 GB    
docker.io/library/phpmyadmin                 latest            f3764e4737b6  18 months ago  571 MB
```