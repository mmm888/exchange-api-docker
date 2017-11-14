# exchange-api-docker

exchange-api-docker is the docker-compose file of [goanda](https://github.com/mmm888/exchange-api-go/tree/master/cmd/goanda)

## Build

**Require setting UserID and API Token for OANDA API**

~~~
git clone https://github.com/mmm888/exchange-api-docker
cd exchange-api-docker
cat << '_EOF_' > build/cmd/secret.go
package exchange

var (
    userID = "REPLACE THIS WITH YOUR ACCOUNT ID, ie 1234567"
    token  = "REPLACE THIS WITH YOUR ACCESS TOKEN"
)
_EOF_

docker-compose up -d
~~~

## Environments

Set env to docker-compose.yml for "goanda influxdb"

~~~
INFLUXDB_ADDRESS     IP Adrress for InfluxDB
INFLUXDB_PORT        Port for InfluxDB
INFLUXDB_DB          Database name for InfluxDB
PAIRCODE             Pair Code (ex: USD_JPY)
LAYOUT               Time format for Golang (ex: 2006-01-02)
START                Start date
END                  End date
GRANULARITY          Granularity to take value (ex: 3H)
~~~

## TODO

* Replace env for "goanda influxdb" to arguments of "goanda" (using flag package)
* Push docker image to Docker Hub
