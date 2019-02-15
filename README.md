# elastic
* Add mappings

```
http://localhost:9200/store
PUT
{
  "mappings": {
    "book": {
      "properties": {
        "title": { 
          "type": "text",
          "analyzer": "english"
        }
      }
    }
  }
}

```

* Validate added mapping

```
http://localhost:9200/store/_analyze
PUT
{
  "field": "title",
  "text":  "The quick Brown Foxes"
}

```
