# docker-siwapp-sf1
Docker container for siwapp sf1

# Introduction

Dockerfile to build a [siwapp](http://www.siwapp.org/) container image.

**Warning!** It uses not official siwapp branch (fork) [darneta/siwapp-sf1](http://github.com/darneta/siwapp-sf1) due to easy setup support.

## Version

Current Version: **0.4.2**

# Installation

Pull the image from the docker index.

```bash
docker pull darneta/siwapp-sf1:latest
```

# Quick Start

Step 1. Launch a mysql container

```bash
docker run --name=mysql-siwapp -d \
  --env='DB_NAME=siwapp' \
  --env='DB_USER=siwapp' --env='DB_PASS=password' \
  --volume=/srv/docker/redmine/mysql:/var/lib/mysql \
  sameersbn/mysql:latest
```

Step 2. Launch a siwapp container

```bash
sudo docker run --name=siwapp -d \
  --link=mysql-siwapp:mysql \
  --publish=10080:80 \
  darneta/siwapp-sf1
```

Step 3. Install siwapp (if not already installed)

Point your browser to `http://localhost:10080` and complete the installation. Database prameters will be set from mysql container so just click next.

# Configuration

## Available environment variables

- **DB_HOST**: The database server hostname. 
- **DB_PORT**: The database server port.
- **DB_NAME**: The database name.
- **DB_USER**: The database user.
- **DB_PASS**: The database password.
