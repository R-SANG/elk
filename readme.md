# ElasticSearch Logstash & Kibana or ELK Stack Sample

Commands that you may want to copy and paste into your Kibana console

```http

GET /_cluster/health

GET /_cat/nodes?v

GET /_cat/indices?v

GET /.kibana/_search
{
  "query": {
    "match_all": {}
  }
}

PUT /pages

GET /_cat/shards?v

DELETE /pages

DELETE /products

PUT /products
{
  "settings": {
    "number_of_shards": 2,
    "number_of_replicas": 2
  }
}

POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}

POST /products/_doc
{
  "name": "Coffee Maker",
  "price": 64,
  "in_stock": 10
}

POST /products/_doc/100
{
  "name": "Machine Maker",
  "price": 99,
  "in_stock": 12
}

GET /products/_doc/100

POST /products/_update/100
{
  "doc": {
    "in_stock": 3
  }
}

POST /products/_update/100
{
  "doc": {
    "tags": ["electronics"]
  }
}

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock--"
  }
}

POST /products/_update/100
{
  "script": {
    "source": "ctx._source.in_stock = 10"
  }
}

DELETE /products/_doc/100

```
