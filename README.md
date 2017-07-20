# couchbase-containerpilot

couchbase + [containerpilot](https://www.joyent.com/containerpilot) docker images for bootstrapping your [autopiloted](https://www.joyent.com/blog/applications-on-autopilot) infractructure

[**Dockerhub Link**](https://hub.docker.com/r/johnhof/couchbase-containerpilot/)

## Configuration

### Couchbase

See the [couchbase image](https://hub.docker.com/_/couchbase/) documentation

### Containerpilot

Uses default containerpilot.json file:

```
{
  "consul": "consul:8500",
  "logging": {
    "level": "INFO",
    "format": "default",
    "output": "stdout"
  },
  "jobs": [
    {
      "name": "couchbase",
      "exec": [
        "/entrypoint.sh",
        "couchbase-server"
      ],
      "port": 8091,
      "health": {
        "exec": "curl --fail -s -o /dev/null http://localhost:8091",
        "interval": 3,
        "ttl": 10
      }
    }
  ]
}

```

Can be overwritten by either:
- Mapping a custom volume/config to `/etc/containerpilot.json`
- Mapping a custom volume/config to a custom location and setting the `CONTAINERPILOT` path to reflect it

#### Consul

Expects DNS entry for `consul`

Expects consul port to be `8500`

Healthcheck hits `/` expecting 200
