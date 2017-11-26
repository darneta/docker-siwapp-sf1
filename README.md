# docker-siwapp-sf1
Docker container for siwapp sf1

# Introduction

Dockerfile to build a [siwapp](http://www.siwapp.org/) container image.

**Warning!** It uses non-official siwapp branch (fork) [darneta/siwapp-sf1](http://github.com/darneta/siwapp-sf1) due to easy setup support and various modifications.

## Version

Current Version: **0.5.2**

# Installation

Pull the image from the docker index.

```bash
docker pull darneta/siwapp-sf1:latest
```

# Quick Start

Step 1. Start all container

```bash
docker-compose up
```

Step 2. Get siwapp container ip address

```
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' dockersiwappsf1_siwapp_1
```

Step 3. Install siwapp (if not already installed)

Point your browser to `http://ip-from-previous-step` and complete the installation. Database prameters will be set from mysql container so just click next.

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
