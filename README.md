# jfrog-monitoring

Docker based solution to monitor JFrog Artifactory and/or JFrog Xray.

[Fluentd](https://www.fluentd.org/) is parsing the log files and exposing them with help of [fluent-prometheus-plugin](https://github.com/fluent/fluent-plugin-prometheus).

[Prometheus](https://prometheus.io/) collects the metrics exposed above.

Eventually [Grafana](https://grafana.com/) queries Prometheus to populate a dashboard.

## Prerequisites

- [docker](https://docs.docker.com/get-docker/)
- [docker-compose](https://docs.docker.com/compose/install/)

## Installation

### Fluent

#### Artifactory
connect into the machine hosting **Artifactory** log files and copy the fluent folder.

run the compose file:
```bash
cd fluent
export FLUENT_CONFIG_FILE=fluent.conf.artifactory
docker-compose up -d
```

Remark:
- make sure that log files are accessible for fluent user

#### Xray (optional)
connect into the machine hosting **Xray** log files and copy the fluent folder.

run the compose file:
```bash
cd fluent
export FLUENT_CONFIG_FILE=fluent.conf.artifactory
docker-compose up -d
```

Remark:
- make sure that log files are accessible for fluent user

### Monitoring
connect into the machine where your monitoring tool suite will be running and copy the *docker-compose.yaml, prometheus folder, grafana folder*.

Prometheus and Grafana are started as a docker-compose instance:
```bash
docker-compose up -d
```

Log into grafana and import the dashboard */Users/jeromep/Desktop/work/src/github/jfrog-monitoring/grafana/JFrog-Platform-Metrics-Dashboard.json*.


