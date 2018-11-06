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

## Every time setup

### Get the Snowplow installation running

```bash
cd example/
docker stack deploy -c docker-compose.yml snowplow-realtime
```

### Send some events

```bash
curl -X POST \
  -d '[{"name":"screen"},{"name":"screen"}]' \
  -H 'Content-Type: application/json; charset=UTF-8' \
  '127.0.0.1:8080/com.snowplowanalytics.iglu/v1?schema=iglu%3Acom.snowplowanalytics.snowplow%2Fscreen_view%2Fjsonschema%2F1-0-0'
curl -X GET 127.0.0.1:8080/i
```

### Setup the web interface

- Go to `http://127.0.0.1:4171/` in your browser
- Go to the `Lookup` tab
- In the `Create Topic/Channel` section:
  - Fill in `bad` as the topic name and `bad_channel` as the channel name and click `Create`
  - Fill in `enriched` as the topic name and `enriched_channel` as the channel name and click `Create`
- Go to `http://127.0.0.1:8081/sub?topic=bad&channel=bad_channel` to see the bad rows
- Go to `http://127.0.0.1:8081/sub?topic=enriched&channel=enriched_channel` to see the enriched
events

![setup](https://github.com/snowplow-incubator/snowplow-on-your-laptop-workshop/raw/master/setup.gif)

### Tear down

```bash
docker stack rm snowplow-realtime
```
