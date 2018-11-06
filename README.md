# Snowplow on your laptop

## Setup required before the workshop

### Install Docker

- For Linux: https://docs.docker.com/install/linux/docker-ce/binaries/ or distribution-specific
instructions
- For Mac: https://docs.docker.com/docker-for-mac/install/
- For Windows: https://docs.docker.com/docker-for-windows/install/

Make sure it worked by running `docker --version` in a terminal.

### Install Git

For all platforms: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

Make sure it works by running `git --version` in a terminal.

## First time setup

Those commands are to be done once, the first time you set this up.

### Clone the Snowplow Docker repository

```bash
git clone https://github.com/snowplow/snowplow-docker.git
```

### Initialize your Docker installation

```bash
docker swarm init
```
