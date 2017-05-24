# Wikidata queries

Examples of Wikidata queries relevent to stuff I work on.


## Source(s) of a taxon name in Wikidata

Data sources for a taxonomic name

```
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX pr: <http://www.wikidata.org/prop/reference/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wd: <http://www.wikidata.org/entity/>

SELECT *
WHERE
{
  ?wikidata wdt:P225 "Mammalia" .
  ?wikidata p:P225 ?statement. 
  ?statement prov:wasDerivedFrom ?provenance .
  ?provenance pr:P248 ?reference .
  ?reference wdt:P1476 ?title .
}
```

[Try it](http://tinyurl.com/n68edwv)


## Find author of taxon name

```
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX pq: <http://www.wikidata.org/prop/qualifier/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX p: <http://www.wikidata.org/prop/>

SELECT *
WHERE
{
  ?wikidata wdt:P225 "Zodariidae" .
  ?wikidata p:P225 ?statement .
  ?statement pq:P405 ?authority .
  ?authority rdfs:label ?name .
  
  FILTER (lang(?name) = 'en')
}
```

[Try it](http://tinyurl.com/lur5xtf)

## Find date of publication

Date of publication of name

```
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX pq: <http://www.wikidata.org/prop/qualifier/>
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX p: <http://www.wikidata.org/prop/>

SELECT *
WHERE
{
  ?wikidata wdt:P225 "Liphistiidae" .
  ?wikidata p:P225 ?statement .
  ?statement pq:P574 ?date .
}
```

[Try it](http://tinyurl.com/kclxpzv)




