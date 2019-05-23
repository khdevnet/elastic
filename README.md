# Elasticsearch

## Commands
### Display current index mappings
```
GET 'localhost:9200/books/_mapping?&pretty'
```

### Update already exists index mapping (you can add only new fields)
```
PUT 'localhost:9200/books/_mapping/fiction?pretty'
{
  "properties": {
    "pages": {
      "type": "integer"
    }
  }
}
```
### Add item to idex
```
POST 'localhost:9200/books/fiction/1?pretty
{
  "name": "Harry Potter",
  "author": "J.K.Rowling",
  "cost": "325.00",
  "Available": "true",
  "publishers": "Bloomsbury",
  "date": "1997-06-27"
}
```
### Add mappings
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
### Validate added mapping
```
http://localhost:9200/store/_analyze
PUT
{
  "field": "title",
  "text":  "The quick Brown Foxes"
}
```

## Notes
### Document
* Basic unit of information to be indexed
* Expressed in JSON
* Resides within an index

### Index
* Collection of similar documents
* Identified by name
* Any number of indices in a cluster
* Different indices for different logical groupings

### Shards
* Split the index across multiple nodes in the cluster

### Shards and Replicas
* An index can be split into multiple shards
* A shard can be replicated zero or more times
* An index in Elasticsearch has 5 shards and 1 replica by default
* Specifying the number of shards is static - can only be done at index creation time
* Specifying the number of replicas is dynamic - can be changed after the index is
created and populated

### TF/IDF Relevance Algorithm
![](https://github.com/khdevnet/elastic/raw/master/src/algorithm.png)

### Data types
![](https://github.com/khdevnet/elastic/raw/master/src/data-types.png)

### Mapping
#### Meta fields
* _source - The original JSON representing the body of the document.
* _all - concatenates contents of all fields into one big string with space delimeter.

