---
title: 'Recording authorship, curation and digital creation with the PAV ontology'
date: Thu, 28 Mar 2013 12:12:55 +0000
draft: false
categories: 
  - Practical Provenance
  - Archive
tags: 
  - PAV
  - PROV
  - provenance
  - vocabulary
aliases:
 - /2022/prov/2013/03/28/pav/
summary: >
    PAV is a lightweight ontology for tracking _Provenance, Authoring and Versioning_.  PAV supplies terms for distinguishing between the different roles of the agents contributing content in current web based systems: _contributors_, _authors_, _curators_ and digital artifact _creators_. The ontology also provides terms for tracking provenance of digital entities that are published on the web and then _accessed_, _transformed_ and _consumed_. 
---

<a href="https://archive.softwareheritage.org/browse/origin/?origin_url=https://github.com/pav-ontology/pav">
    <img src="https://archive.softwareheritage.org/badge/origin/https://github.com/pav-ontology/pav/">
</a>

**PAV** [[archived 2012-02-18](https://web.archive.org/web/20120218065441/http://code.google.com:80/p/pav-ontology/wiki/Homepage), now [GitHub pav-ontology/pav](https://github.com/pav-ontology/pav/), [archived](https://archive.softwareheritage.org/swh:1:dir:ef7139eb34d6b9d6e33ce69bf823d97a747490c1)] is a lightweight ontology for tracking _Provenance, Authoring and Versioning_. PAV supplies terms for distinguishing between the different roles of the agents contributing content in current web based systems: _contributors_, _authors_, _curators_ and digital artifact _creators_. 

The ontology also provides terms for tracking provenance of digital entities that are published on the web and then _accessed_, _transformed_ and _consumed_. PAV version 2.1.1 was ~~[released on 2013-03-27](https://code.google.com/p/pav-ontology/wiki/Versions#PAV_ontology_v2.1.1_(2013-03-26))~~ [Google Code retired, [archived 2016-06-08](https://web.archive.org/web/20160806140733/https://code.google.com/p/pav-ontology/wiki/Versions#PAV_ontology_v2.1.1_(2013-03-26)); now on [GitHub](https://github.com/pav-ontology/pav/releases/tag/2.1.0)], making PAV an extension of the W3C provenance ontology [PROV-O](http://www.w3.org/TR/prov-o/), thus enabling interoperability between PAV and PROV-compliant tools such as [ProvToolbox](https://github.com/lucmoreau/ProvToolbox) [[archived](https://archive.softwareheritage.org/swh:1:dir:c79ff9453a5dd19629fab080e3c86ebb94250a1e)].


Overview
--------

![Diagram overview of PAV: a resource has pav attributes like createdBy, contributedBy to Person agents. From the resource,createdWith, retrievedBy etc. go to Software agents, and providedBy to Organization agents. createdAt goes to a Location, and sourceAccessedAt, derivedFrom, retrievedFrom to another resource](pav-simpler1.png "UML-like overview of PAV ontology")

_Note: PAV does not define any classes, and the PAV properties do not put any explicit restrictions on their domain/ranges. Therefore the classes above, like "another resource", are only for illustration of typical use. The diagram above does not show data properties attached to resources, like `pav:createdOn`._

Example
-------

Here's an example of using PAV: 

```turtle
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix pav: <http://purl.org/pav/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix : <http://example.com/blog#> .

<http://example.com/blog.html> 
   pav:createdBy :alice ;
   pav:createdWith :wordpress ;

   pav:importedFrom <http://example.com/data.csv> ;
   pav:importedBy :csv2html ;

   pav:authoredBy :bob ;
   pav:curatedBy :charlie ;

   pav:authoredOn "2012-12-24T15:15:15Z"^^xsd:dateTime ;
   pav:importedOn "2013-03-27T10:06:17Z"^^xsd:dateTime .


:alice foaf:name "Alice" .
:bob foaf:name "Bob" .
:charlie foaf:name "Charlie" .
:csv2html a prov:SoftwareAgent ;
    foaf:homepage <https://github.com/mrc/csv2html> .
:wordpress a prov:SoftwareAgent ;
    foaf:homepage <http://wordpress.org/> .
```


This example shows how the blog post `http://example.com/blog.html` was [createdBy](http://purl.org/pav/html#http://purl.org/pav/createdBy) Alice. The blog post was [createdWith](http://purl.org/pav/html#http://purl.org/pav/createdWith) the software Wordpress. The content of the blog was [importedFrom](http://purl.org/pav/html#http://purl.org/pav/importedFrom) `http://example.com/data.csv` (presumably a CSV file), and this was [importedBy](http://purl.org/pav/html#http://purl.org/pav/importedBy) the script csv2html. 

Although Alice is the _creator_ (as she made the blog post), `http://example.com/blog.html` is [authoredBy](http://purl.org/pav/html#http://purl.org/pav/authoredBy) Bob, he made the original data and therefore also is the _author_ of (the content of) the blog post. 

The post was [curatedBy](http://purl.org/pav/html#http://purl.org/pav/curatedBy) Charlie, who perhaps edited the CSV (or HTML) to include the correct column headers. We also notice that the blog was [importedOn](http://purl.org/pav/html#http://purl.org/pav/importedOn) March 2013, while the content was [authoredOn](http://purl.org/pav/html#http://purl.org/pav/authoredOn) December 2012. We don't know when Charlie curated it, although this could have been provided with [curatedOn](http://purl.org/pav/html#http://purl.org/pav/curatedOn).

Additional PAV properties allows specifying attributions like [contributors](http://purl.org/pav/html#http://purl.org/pav/contributedBy), the [provider](http://purl.org/pav/html#http://purl.org/pav/providedBy) in addition to other kind of sources, such as [direct downloading](http://purl.org/pav/html#http://purl.org/pav/retrievedFrom), [verification against source material](http://purl.org/pav/html#http://purl.org/pav/sourceAccessedAt) and [derivation](http://purl.org/pav/html#http://purl.org/pav/derivedFrom) when further refinements have been made. Data can be given a [version](http://purl.org/pav/html#http://purl.org/pav/version) number, indicate its lineage to a [previous version](http://purl.org/pav/html#http://purl.org/pav/previousVersion), and indicate when a source was [last updated](http://purl.org/pav/html#http://purl.org/pav/lastUpdatedOn).

The PAV approach
----------------

The goal of PAV is to provide a lightweight, straight forward way to give the essential information about _authorship_, _provenance_ and _versioning_, and therefore these properties are described directly on the published resource. 

As such, PAV does not define any classes or restrict domain/ranges, as all properties are applicable to any online resource. 

This "flat" approach mean that it is easy to use and query PAV without a deep understanding of provenance models, but at a small cost that more complex relationships are not expressed. 

For instance, `pav:authoredBy` allows multiple authors, but if there are multiple authors we won't know who wrote what; or when they did so. Such details can be included alongside PAV using other PROV statements.

Combining PAV with other PROV extensions
----------------------------------------

Here's an example combining PAV with another PROV extension, the [Provenance Vocabulary](http://trdf.sourceforge.net/provenance/ns.html). 

```turtle
@prefix pav: <http://purl.org/pav/> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix prv: <http://purl.org/net/provenance/core#> .
@prefix prvTypes: <http://purl.org/net/provenance/types#> .
@prefix http: <http://www.w3.org/2006/http#> .

<http://example.com/data.csv> a prv:DataItem, prov:Entity ;
    pav:retrievedFrom <http://example.org/originalData> ;
    prv:retrievedBy [ a prvTypes:HTTPBasedDataAccess ;
        prv:accessedResource <http://example.org/originalData> ;
        prvTypes:exchangedHTTPMessage [ a http:Request ;
            http:httpVersion "1.1" ;
            http:methodName "GET" ;
            http:requestURI "http://example.org/originalData" ;
            http:headers ( [ a http:MessageHeader ;
                             http:fieldName "Accept" ;
                             http:fieldValue "text/csv" ] )
        ]
    ] .
``` 

This example shows how `http://example.com/data.csv` was downloaded from `http://example.org/originalData` with HTTP 1.1 and requesting `Accept: text/csv` by content negotiation. 

The PAV term `pav:retrievedFrom` gives the short-cut to the original data, while `prv:retrievedBy` gives details of the transport and content-negotiation used in the download. 

By combining vocabularies in such an approach it is possible to query the provenance for PAV statements in order to get a general overview of the provenance, and then explore other PROV statements for more specific details, which structure might not be known in advance.

Using PAV
---------

To use PAV, import the [PAV ontology](http://purl.org/pav/) from the namespace http://purl.org/pav/ and read the [PAV documentation](http://purl.org/pav/html). The ~~[PAV wiki pages](https://code.google.com/p/pav-ontology/wiki/Homepage)~~ [Google Code retired, [archived 2012-02-18](https://web.archive.org/web/20120218065441/http://code.google.com:80/p/pav-ontology/wiki/Homepage), see [GitHub Wiki]()] contain details about the ~~[PAV versions](https://code.google.com/p/pav-ontology/wiki/Versions)~~ [[archived 2016-08-06](https://web.archive.org/web/20160806140733/https://code.google.com/p/pav-ontology/wiki/Versions), see [GitHub Wiki](https://github.com/pav-ontology/pav/wiki/Versions)]. If your ontology extends or uses PAV, you can use either:

```turtle
owl:imports <http://purl.org/pav/>
```

for the latest version (which might at some point include additional properties), or

```turtle
owl:imports <http://purl.org/pav/2.1>
```

for the latest patch version of 2.1 (ie. no new terms will be added later).

Extracting PROV-O statements
----------------------------

As PAV is meant as a lightweight ontology, the inferred PROV-O statements are not usually explicitly included. Any OWL or RDFS reasoner should be able to infer the PROV-O statements as long as the PAV ontology is imported from http://purl.org/pav/ 

As an example of PAV interoperability with PROV, we built a [Taverna workflow](http://www.myexperiment.org/workflows/3424 "Visualize PAV provenance as SVG") which uses the ~~[OWL reasoner Pellet](http://clarkparsia.com/pellet/)~~ [[archived 2014-02-07](https://web.archive.org/web/20140207202729/http://clarkparsia.com/pellet/), now [GitHub stardog-union/pellet](https://github.com/stardog-union/pellet), [archived](https://archive.softwareheritage.org/swh:1:dir:d841895e37a8d2b6630b082096f1260431a17416)] to infer PROV statements, and then visualize this as SVG using the [PROV toolbox](https://github.com/lucmoreau/ProvToolbox). Here's the diagram (as PNG) visualizing the [PAV example](https://gist.github.com/stain/5262169) from the beginning of this page: 

![pav-example](pav-example.png)
