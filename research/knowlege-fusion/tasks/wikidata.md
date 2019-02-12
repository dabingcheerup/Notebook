# wikidata

## Ontology - Digraph：Test1 Use sample truthy dump

### S1: Download RDF dumps \(Truthy\)

#### 为什么要Truth有？

因为缩小了数据量，没有claim quantifiers。

#### 直接下载

太慢了，要4小时

1. 
#### 用程序

不知道怎么改

1. Library Keyword search：Truthy  - To find methods
   1. **RdfSerializationExample.java** - generate RDF dump from JSON dump
   2. This paper introduces the [RDF exports of Wikidata](http://tools.wmflabs.org/wikidata-exports/rdf/). The software used to generate the exports is [Wikidata Toolkit](https://www.mediawiki.org/wiki/Wikidata_Toolkit).

      1. [wikidata-taxonomy.nt.gz](https://tools.wmflabs.org/wikidata-exports/rdf/exports/20160801/wikidata-taxonomy.nt.gz) \(2820385 triples, 11.1MiB\) \([sample](https://tools.wmflabs.org/wikidata-exports/rdf/exports/20160801/sample-wikidata-taxonomy.nt)\) OWL/RDF dump the class hierarchy of Wikidata. Statements of property "subclass of" \(P279\) that have no qualifiers are exported using rdfs:subClassOf. All items that are used like classes in "subclass of" \(P279\) or "instance of" \(P31\) are declared as OWL classes.
      2. [wikidata-instances.nt.gz](https://tools.wmflabs.org/wikidata-exports/rdf/exports/20160801/wikidata-instances.nt.gz) \(17894112 triples, 77.3MiB\) \([sample](https://tools.wmflabs.org/wikidata-exports/rdf/exports/20160801/sample-wikidata-instances.nt)\) OWL/RDF dump of all class membership information in Wikidata. Statements of property "instance of" \(P31\) that have no qualifiers are exported using rdf:type. Relevant class declarations are found in wikidata-taxonomy.nt.gz.
      3. [wikidata-property-taxonomy.nt.gz](https://tools.wmflabs.org/wikidata-exports/rdf/exports/20160801/wikidata-property-taxonomy.nt.gz) \(2789 triples, 10.4KiB\) \([sample](https://tools.wmflabs.org/wikidata-exports/rdf/exports/20160801/sample-wikidata-property-taxonomy.nt)\) OWL/RDF dump the class hierarchy of Wikidata Properties.

      =====================================================================
2. **To Do List**

* 读 [RDF exports of Wikidata](http://tools.wmflabs.org/wikidata-exports/rdf/)，了解怎么用wikidata toolkit 生以上RDF exports
* // 找到wikidata toolkit中生成RDF exports的代码，作修改，生成最新的RDF exports

### S2: Clean & Parse RDF 

RDF format: Using URIs for entities - [http://www.wikidata.org/entity/&lt;id&gt;](http://www.wikidata.org/entity/<id>)

* [ ] Use id to get label
* [ ] then convert to triples: subject label, property label, object label

### S2: Extract subclassOf / instanceOf - Ontology Graph

* [ ] Only extract those triples having subclassOf and instanceOf

### S3: Triples - Digraph

## Ontology - Digraph：Test2 Use  truthy dump

### S1: Download RDF dumps \(Truthy\)

#### 参考wikidata, parse compressed dump file, then write to compressed dump file

1. Rewrite read and write function

### S2: Clean & Parse RDF 

RDF format: Using URIs for entities - [http://www.wikidata.org/entity/&lt;id&gt;](http://www.wikidata.org/entity/<id>)

#### Extract subclassOf / instanceOf triples

1. example triple: Q8 P31 Q34567 
2. result format1: 8 34567
   1. Remove "Q"  for memory concern
3. result format2: happiness emotion
   1. Use id to get label

### S3: Triples - Digraph

#### Implement digraph from parsed RDF by adjacency list



