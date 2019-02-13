# clickhouse-tutorial

## Documentation
* ClickHouse main site: https://clickhouse.yandex/
* ClickHouse tutorial: https://clickhouse.yandex/tutorial.html
* ClickHouse technical documentation: https://clickhouse.yandex/docs/en/
* Docker istallation documentation: https://www.docker.com/get-started
* ClickHouse Server Docker Image: https://hub.docker.com/r/yandex/clickhouse-server/
* Tabix documentation: https://github.com/tabixio/tabix

## Command line commands
* Next command starts clickhouse server:
```
docker run -d -p 8123:8123 --name some-clickhouse-server --ulimit nofile=262144:262144 yandex/clickhouse-server
```
* Next command runs console client for data querying and connect it to clickhouse server:
```
docker run -it --rm --link some-clickhouse-server:clickhouse-server yandex/clickhouse-client --multiline --host clickhouse-server
```
* Next command loads sample dataset to clickhouse:
```
xz -v -c -d < ontime.csv.xz | docker run -i --rm --link some-clickhouse-server:clickhouse-server yandex/clickhouse-client --multiline --host clickhouse-server --max_insert_block_size=100000 --query="INSERT INTO ontime FORMAT CSV"
```
* Next command starts graphical user web interface Tabix:
```
docker run -d -p 8080:80 spoonest/clickhouse-tabix-web-client
```
