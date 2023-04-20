# Elasticsearch Docker Compose

## Starting
Bring-up the Elasticsearch container via:
```bash
docker-compose up -d
```

It'll create a Elasticsearch server:
Username: `elastic`
Password: `secret`
Host: `127.0.0.1:9201`

## Access
Access it via the info above from your host (Laptop):
```
curl --insecure https://elastic:secret@127.0.0.1:9201
```

## Hello World
Check if we have access to the endpoints, create a document, get its index data and retrieve the item.

```bash
curl --insecure https://elastic:secret@127.0.0.1:9201
# Response:
{
  "name" : "fb5cfd5c4ea7",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "jLrev6nzT3KQhOADCfAqLw",
  "version" : {
    "number" : "8.7.0",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "09520b59b6bc1057340b55750186466ea715e30e",
    "build_date" : "2023-03-27T16:31:09.816451435Z",
    "build_snapshot" : false,
    "lucene_version" : "9.5.0",
    "minimum_wire_compatibility_version" : "7.17.0",
    "minimum_index_compatibility_version" : "7.0.0"
  },
  "tagline" : "You Know, for Search"
}

curl -XPOST -H "Content-Type: application/json" --insecure https://elastic:secret@127.0.0.1:9201/products/_doc/1 -d '
{
  "id": 1,
  "name": "LG G5"
}'
# Response:
{"_index":"products","_id":"1","_version":1,"result":"created","_shards":{"total":2,"successful":1,"failed":0},"_seq_no":0,"_primary_term":1}

curl --insecure https://elastic:secret@127.0.0.1:9201/products/
# Response:
{"products":{"aliases":{},"mappings":{"properties":{"id":{"type":"long"},"name":{"type":"text","fields":{"keyword":{"type":"keyword","ignore_above":256}}}}},"settings":{"index":{"routing":{"allocation":{"include":{"_tier_preference":"data_content"}}},"number_of_shards":"1","provided_name":"products","creation_date":"1681981890121","number_of_replicas":"1","uuid":"eoUDl8d9T0COd5e8TtLLLw","version":{"created":"8070099"}}}}}

curl --insecure https://elastic:secret@127.0.0.1:9201/products/_doc/1
# Response
{"_index":"products","_id":"1","_version":1,"_seq_no":0,"_primary_term":1,"found":true,"_source":
{
  "id": 1,
  "name": "LG G5"
}}
```

## View Logs
See the Elasticsearch server logs via:
```bash
docker-compose logs -f --tail 1000
```

## Sources
- https://hub.docker.com/_/elasticsearch
- https://www.elastic.co/guide/en/welcome-to-elastic/current/getting-started-general-purpose.html