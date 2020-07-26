# CISC 525 Module 10 Output of Exercise #5.

You must provide this output as a part of your homework assignment.
You must share this repository with me
For each command you run on Kibana's web console, make sure to provide the input and output of the
command as follows:

## Kibana Console

- command input: **Checking the cluster health.**

```http

GET /_cluster/health
```

- command output

```json
{
  "cluster_name" : "elasticsearch",
  "status" : "yellow",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  "active_primary_shards" : 4,
  "active_shards" : 4,
  "relocating_shards" : 0,
  "initializing_shards" : 0,
  "unassigned_shards" : 1,
  "delayed_unassigned_shards" : 0,
  "number_of_pending_tasks" : 0,
  "number_of_in_flight_fetch" : 0,
  "task_max_waiting_in_queue_millis" : 0,
  "active_shards_percent_as_number" : 80.0
}
```

- alternative curl:
  
```bash
curl -XGET "http://localhost:9200/_cluster/health"
```

- command input: Listing the cluster's nodes

```http
GET /_cat/nodes?v
```

- command output:

```json
ip        heap.percent ram.percent cpu load_1m load_5m load_15m node.role master name
127.0.0.1           33          38  11    0.75    0.65     0.65 dilm      *      student-VirtualBox
```

- curl command:

```bash
curl -XGET "http://localhost:9200/_cat/nodes?v"
```

- command input: Listing the cluster's indicies

```http

GET /_cat/indices?v
```

- command output

```json

health status index                    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   .kibana_task_manager_1   9D3oQE8zQ2-q0qM4XCMITg   1   0          2            1     26.9kb         26.9kb
green  open   .apm-agent-configuration DvPDzd-uRPWLOWR-FlVKbQ   1   0          0            0       283b           283b
green  open   .kibana_1                Tye9xrNRSNufstAaXD6HeA   1   0         22            8     46.4kb         46.4kb
yellow open   products                 g_56tv_kRLS3A-WQ7Lfnhg   1   1          1            0        4kb            4kb

```

- alternative curl:
  
```bash

curl -XGET "http://localhost:9200/_cat/indices?v"
```

- command input: Test search query

```http

GET /.kibana/_search
{
  "query": {
    "match_all": {}
  }
}
```

- command output

```json
{
  "took" : 4,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 22,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "space:default",
        "_score" : 1.0,
        "_source" : {
          "space" : {
            "name" : "Default",
            "description" : "This is your default space!",
            "color" : "#00bfb3",
            "disabledFeatures" : [ ],
            "_reserved" : true
          },
          "type" : "space",
          "references" : [ ],
          "migrationVersion" : {
            "space" : "6.6.0"
          },
          "updated_at" : "2020-03-21T11:56:30.286Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "config:7.6.1",
        "_score" : 1.0,
        "_source" : {
          "config" : {
            "buildNum" : 29118
          },
          "type" : "config",
          "references" : [ ],
          "updated_at" : "2020-03-21T11:56:40.954Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "telemetry:telemetry",
        "_score" : 1.0,
        "_source" : {
          "telemetry" : {
            "userHasSeenNotice" : true
          },
          "type" : "telemetry",
          "references" : [ ],
          "updated_at" : "2020-03-21T11:56:59.847Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:sampleDataConfirm",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-21T12:31:48.378Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:GET_cat.shards",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 2
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-25T00:34:16.275Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:console:DELETE_delete",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 2
          },
          "type" : "ui-metric",
          "updated_at" : "2020-03-25T00:47:47.403Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:welcomeScreenMount",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 3
          },
          "type" : "ui-metric",
          "updated_at" : "2020-07-25T20:20:59.311Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:Kibana_home:sampleDataDecline",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 2
          },
          "type" : "ui-metric",
          "updated_at" : "2020-07-25T20:28:30.575Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "maps-telemetry:maps-telemetry",
        "_score" : 1.0,
        "_source" : {
          "maps-telemetry" : {
            "settings" : {
              "showMapVisualizationTypes" : false
            },
            "indexPatternsWithGeoFieldCount" : 0,
            "mapsTotalCount" : 0,
            "timeCaptured" : "2020-07-26T03:41:45.020Z",
            "attributesPerMap" : {
              "dataSourcesCount" : {
                "min" : 0,
                "max" : 0,
                "avg" : 0
              },
              "layersCount" : {
                "min" : 0,
                "max" : 0,
                "avg" : 0
              },
              "layerTypesCount" : { },
              "emsVectorLayersCount" : { }
            }
          },
          "type" : "maps-telemetry",
          "references" : [ ],
          "updated_at" : "2020-07-26T03:41:45.020Z"
        }
      },
      {
        "_index" : ".kibana_1",
        "_type" : "_doc",
        "_id" : "ui-metric:kibana-user_agent:Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0",
        "_score" : 1.0,
        "_source" : {
          "ui-metric" : {
            "count" : 1
          },
          "type" : "ui-metric",
          "references" : [ ],
          "updated_at" : "2020-07-26T03:45:04.686Z"
        }
      }
    ]
  }
}

```

- alternative curl:
  
```bash
curl -XGET "http://localhost:9200/.kibana/_search" -H 'Content-Type: application/json' -d'{  "query": {    "match_all": {}  }}'
```

- command input: Creating a new index

```http

PUT /pages
```

- command output

```json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "pages"
}

```

- alternative curl:
  
```bash
curl -XPUT "http://localhost:9200/pages"
```

- command input: Listing the cluster;s shards

```http

GET /_cat/shards?v
```

- command output

```json
index                    shard prirep state      docs  store ip        node
products                 0     p      STARTED       1    4kb 127.0.0.1 student-VirtualBox
products                 0     r      UNASSIGNED                       
.kibana_task_manager_1   0     p      STARTED       2 26.9kb 127.0.0.1 student-VirtualBox
.kibana_1                0     p      STARTED      22 52.2kb 127.0.0.1 student-VirtualBox
pages                    0     p      STARTED       0   230b 127.0.0.1 student-VirtualBox
pages                    0     r      UNASSIGNED                       
.apm-agent-configuration 0     p      STARTED       0   283b 127.0.0.1 student-VirtualBox

```

- alternative curl:
  
```bash

curl -XGET "http://localhost:9200/_cat/shards?v"
```

- command input: Deleting an index

```http

DELETE /pages
```

- command output

```json
{
  "acknowledged" : true
}

```

- alternative curl:
  
```bash

curl -XDELETE "http://localhost:9200/pages"
```

- command input: Deleteing an index.

```http

DELETE /products
```

- command output

```json
{
  "acknowledged" : true
}

```

- alternative curl:
  
```bash

curl -XDELETE "http://localhost:9200/products"
```

- command input: Indexing document with auto generated ID

```http

POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}

```

- command output

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "STtfiXMB6jJ4Lj8r32hx",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 4,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}
```

- alternative curl:
  
```bash
curl -XPOST "http://localhost:9200/products/_doc" -H 'Content-Type: application/json' -d'{  "name": "Coffee Maker",  "price": 64,  "in_stock": 10}'
```

- command input: Indexing document with customer ID.

```http

PUT /products/_doc/100
{
  "name": "TOASTER",
  "price": 49,
  "in_stock": 4
}
```

- command output

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 2,
  "result" : "updated",
  "_shards" : {
    "total" : 4,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 7,
  "_primary_term" : 1
}


```

- alternative curl:
  
```bash
curl -XPUT "http://localhost:9200/products/_doc/100" -H 'Content-Type: application/json' -d'{  "name": "TOASTER",  "price": 49,  "in_stock": 4}'
```

- command input: Retrieving documents by ID

```http
GET /products/_doc/100
```

- command output

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 1,
  "_seq_no" : 0,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "name" : "Machine Maker",
    "price" : 99,
    "in_stock" : 12
  }
}

```

- alternative curl:
  
```bash

curl -XGET "http://localhost:9200/products/_doc/100"
```

- command input: Updating an existing field

```http

POST /products/_update/100
{
  "doc": {
    "in_stock": 3
  }
}
```

- command output

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 2,
  "result" : "noop",
  "_shards" : {
    "total" : 0,
    "successful" : 0,
    "failed" : 0
  },
  "_seq_no" : 1,
  "_primary_term" : 1
}


```

- alternative curl:
  
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "doc": {    "in_stock": 3  }}'
```


- command input: Adding a new field

```http
POST /products/_update/100
{
  "doc": {
    "tags": ["electronics"]
  }
}
```

- command output

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 3,
  "result" : "updated",
  "_shards" : {
    "total" : 4,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 2,
  "_primary_term" : 1
}

```

- alternative curl:
  
```bash
curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "doc": {    "tags": ["electronics"]  }}'
```

- command input: Reducing the current value of in_stock by one.

```http

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock--"
  }
}
```

- command output

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 4,
  "result" : "updated",
  "_shards" : {
    "total" : 4,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 3,
  "_primary_term" : 1
}

```

- alternative curl:
  
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source": "ctx._source.in_stock--"  }}'
```

- command input: Assigning an arbitrary value to in_stock.

```http

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock = 10"
  }
}
```

- command output

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 5,
  "result" : "updated",
  "_shards" : {
    "total" : 4,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 4,
  "_primary_term" : 1
}

```

- alternative curl:
  
```bash

curl -XPOST "http://localhost:9200/products/_update/100" -H 'Content-Type: application/json' -d'{  "script": {    "source": "ctx._source.in_stock = 10"  }}'
```

- command input: DEleting documents

```http
DELETE /products/_doc/100
```

- command output

```json
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "100",
  "_version" : 6,
  "result" : "deleted",
  "_shards" : {
    "total" : 4,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 5,
  "_primary_term" : 1
}


```

- alternative curl:
  
```bash

curl -XDELETE "http://localhost:9200/products/_doc/100"
```


