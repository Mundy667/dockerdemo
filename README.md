# Docker Demo

Introduction to Docker  and the NetApp Docker Volume Plugin (nDVP)

## Instructions

### Step 1: Hello World

Show the hello-world container

```bash
docker run hello-world
```

Show running containers:

```bash
docker ps
```

Show images:

```bash
docker images ls
```

### Step 2: A simple service in a containers

GoTo Folder demo01Web

Show and explain ```Dockerfile```

Show code folder that is copied into the container

Build the container

```bash
docker build -t halloweltwebserver:v1 .
```

and run it

```bash
docker run -d -p 80:80 halloweltwebserver:v1
```

Open Browser and show Website on Host-IP:80

Show how more instances can be startet. No download is needed since images are already here.

```bash
docker run -d -p 5000:80 halloweltwebserver:v1
```

Open this Webserver at Host-IP:5000

Stop everything!!!  

### Step3: Basics in the NetApp-Docker-Volume Plugin

Tip: Install before the demo. In case of problems.

But show how easy it is to install the plugin by open the readthedocs-site and highlighting the command.

https://netapp-trident.readthedocs.io/

Then go to the host and show the config-file that is used when installing the plugin.

```bash
cat /etc/netappdvp/config.json
```

Show persistent volumes:

```bash
docker volume ls
```

Now manually create a new volumes

```bash
docker volume create -d netapp --name my_vol --opt size=10G
docker volume ls
```

Show the created volume via SystemManager on the connected NetApp System


### Step4: A complete application stack with different services per container

Goto the demo02App - Folder

Show ```Dockerfile```

First, build the current codebase:

```bash
docker build . -t "webapp_build"
```

Let's make sure it was built successfully:

```bash
docker images
```

Show and explain the ```docker-compose.yml```
This is the Application Stack. A webserver, the code and Database resing on a netapp volume.

Let's show our current Docker Volumes:

```bash
docker volume ls
```

Bring up the application stack:

```bash
docker-compose up
```

Show the new created netapp volume.
Show the application.
