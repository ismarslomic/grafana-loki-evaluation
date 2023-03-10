# Evaluation of Grafana Loki for log aggregation

> Example for evaluating use of Grafana Loki for log aggregation, see [docker-compose.yaml](docker-compose.yaml) for
> which containers are used. Based
> on [Getting started with Grafana Loki](https://grafana.com/docs/loki/latest/getting-started/)


## Start the containers
```bash
docker compose up -d
```

Open Grafana and head to the Explore tab http://localhost:3000/explore.

## Query examples

To see all the log lines that flog has generated:

```text
{container="flog"}
```

The flog app will generate log lines for invented HTTP requests. To see all GET log lines, enter the query:

```text
{container="flog"} |= "GET"
```

For POST methods:

```text
{container="flog"} |= "POST"
```

To see every log line with a 401 status (unauthorized error):

```text
{container="flog"} | json | status="401"
```

To see every log line other than those that contain the value 401:

```text
{container="flog"} != "401"
```
