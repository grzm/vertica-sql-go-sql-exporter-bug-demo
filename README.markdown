# Demonstration of possible vertica-sql-go concurrency bug

Leverages the
[free/sql_exporter](https://github.com/free/sql_exporter) Prometheus
exporter.

## Set up the demo

Creates a local `GOPATH` environment and fetches dependencies.

```
source bin/demo.env
bin/setup
```

Create the `sql_exporter` config file by copying the provided template ...

```
cp sql_exporter.template.yml sql_exporter.yml
```

... and updating the `data_source_name` value in your favorite editor.

```
  data_source_name: "vertica://dbadmin:PASSWORD@HOST:5433/DBNAME"
```

Start the `sql_exporter`.

```
sql_exporter
```

In a separate session, call the `sql_exporter` scrape API to trigger
calls to Vertica.

```
curl http://localhost:9399/metrics
```
