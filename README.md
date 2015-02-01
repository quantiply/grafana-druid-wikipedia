An example dashboard using Grafana with Druid

## Install ZooKeeper
[Download](http://zookeeper.apache.org/releases.html#download) and run it with default configuration.

## Install Druid

[Download](http://druid.io/downloads.html) the latest stable release of Druid.

Run the example server script and choose wikipedia.  This will connect to the Wikipedia IRC feed of edits and start indexing them in Druid.

```
./run_example_server.sh
This will run a stand-alone version of Druid
Cleaning up from previous run..
Please specify an example type.
Examples availables:
rabbitmq rand twitter webstream wikipedia
> wikipedia
```

Example using Grafana with Druid

## Setup Web Server/Proxy
Install a web server and set it up to proxy Druid API calls so the browser doesn't complain about origin issues.

For nginx, add this

```
    location /druid/ {
        proxy_pass  http://127.0.0.1:8083/druid/;
    }
```

## Install Grafana plugins

Clone or download [this repo](https://github.com/Quantiply/grafana-plugins)

## Install this repo
Clone or download it

## Install Grafana

[Download](http://grafana.org/download/) version 1.9.x of Grafana and untar it.

Create symbolic links to the config and the plugins

```
cd grafana-1.9.1
ln -s ~/Work/grafana-druid-wikipedia/config.js config.js
ln -s ~/Work/grafana-druid-wikipedia/dashboards/wikipedia.json app/dashboards/wikipedia.json
ln -s ~/Work/grafana-plugins/features plugins/features
```
