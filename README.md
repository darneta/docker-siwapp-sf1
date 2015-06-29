# docker-siwapp-sf1
Docker container for siwapp sf1

# Introduction

Dockerfile to build a [siwapp](http://www.siwapp.org/) container image.

**Warning!** It uses non-official siwapp branch (fork) [darneta/siwapp-sf1](http://github.com/darneta/siwapp-sf1) due to easy setup support and various modifications.

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
  --volume=/srv/docker/siwapp/mysql:/var/lib/mysql \
  sameersbn/mysql:latest
```

Step 2. Launch a postfix container

```bash
docker run -d --name siwapp-postfix \
 --env="maildomain=your_domain.com" \
 --env="smtp_user=siwapp:siwapp" \
 catatnight/postfix
```

Step 3. Launch a siwapp container

```bash
docker run --name=siwapp -d \
  --link=mysql-siwapp:mysql \
  --link=siwapp-postfix:postfix \
  --env="SMTP_USER=siwapp" \
  --env="SMTP_PASS=siwapp" \
  --env="SMTP_HOST=postfix" \
  --env="SMTP_PORT=25" \
  --publish=10080:80 \
  darneta/siwapp-sf1
```

Step 4. Install siwapp (if not already installed)

Point your browser to `http://localhost:10080` and complete the installation. Database prameters will be set from mysql container so just click next.

# Configuration

## Available environment variables

- **DB_HOST**: The database server hostname. 
- **DB_PORT**: The database server port.
- **DB_NAME**: The database name.
- **DB_USER**: The database user.
- **DB_PASS**: The database password.
- **SMTP_USER**: The SMTP user.
- **SMTP_PASS**: The SMTP pass.
- **SMTP_HOST**: The SMTP host.
- **SMTP_PORT**: The SMTP port.
