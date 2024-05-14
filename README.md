# Local monitoring with a containerized Kibana Dashboard


# Elastic Kibana
Elastic Kibana is a visualization and management tool for Elasticsearch that allows users to visualize data, create dashboards, and manage the Elastic Stack.

## How-to Install Kibana with Docker
https://www.elastic.co/guide/en/kibana/current/docker.html <br>
https://www.elastic.co/guide/en/kibana/8.13/settings.html  <br>
https://hub.docker.com/_/kibana  <br>
https://gist.github.com/technige/02ddb309fd7c23c4649995b1a2b80e93  <br>

## Build
docker build -t kibana-monitor .

## Run
```
docker run -d --name kibana-monitor -p 5601:5601 \
  -e ELASTICSEARCH_HOSTS="http://your-elasticsearch-url:9200" \
  -e ELASTICSEARCH_USERNAME="your-username" \
  -e ELASTICSEARCH_PASSWORD="your-password" \
  kibana-monitor
```


# Elastic Heartbeat
Heartbeat is an Elastic Beat specifically created for uptime monitoring

## How-to Install Heartbeat with Docker
https://www.elastic.co/guide/en/beats/heartbeat/current/heartbeat-installation-configuration.html <br>
https://www.elastic.co/guide/en/beats/heartbeat/current/running-on-docker.html

## Example
```
heartbeat.monitors:
- type: http
  name: "guldmand_com_monitor"
  schedule: '@every 5m'  # Runs the check every 5 minutes
  urls: ["http://guldmand.com"]
  timeout: 10s
  check.response:
    status: 200  # Checks for a 200 OK response

output.elasticsearch:
  hosts: ["your-elasticsearch-url:9200"]
  username: "your-username"
  password: "your-password"
```


# Elastic Filebeat

## Build
docker build -t my-filebeat .

## Run
docker run -d --name=my-filebeat \
  --volume=/path/on/host/to/test/logs:/path/to/test/logs \
  my-filebeat