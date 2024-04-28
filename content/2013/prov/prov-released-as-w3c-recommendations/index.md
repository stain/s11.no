---
title: 'PROV released as W3C Recommendations'
date: Wed, 01 May 2013 10:09:04 +0000
categories:
    - Practical Provenance
    - Archive
tags: ['PROV', 'W3C']
aliases:
    - /2022/prov/2013/05/01/prov-released-as-w3c-recommendations/
---

> The [Provenance Working Group](http://www.w3.org/2011/prov/) was chartered to develop a framework for interchanging provenance on the Web. The Working Group has now published the PROV Family of Documents as W3C Recommendations, along with corresponding supporting notes. You can find a complete list of the documents in the [PROV Overview Note](http://www.w3.org/TR/2013/NOTE-prov-overview-20130430/).  
> PROV enables one to represent and interchange provenance information using widely available formats such as [RDF](http://www.w3.org/TR/prov-o/) and [XML](http://www.w3.org/TR/prov-xml/). In addition, it provides definitions for [accessing provenance information](http://www.w3.org/TR/prov-aq/), [validating](http://www.w3.org/TR/prov-constraints/) it, and [mapping to Dublin Core](http://www.w3.org/TR/prov-dc/). Learn more about the [Semantic Web](http://www.w3.org/2001/sw/).

```turtle
@prefix prov: <http://www.w3.org/ns/prov#> .
<#quote> prov:wasQuotedFrom <http://www.w3.org/News/2013#entry-9805> .
```

This means the PROV data model and specifications are released and official recommendations, and can be used as a stable platform for expressing and exploring provenance data across the web. 

Practically speaking, this blog would recommend you start with the [PROV primer](http://www.w3.org/TR/prov-primer/ "W3C PROV primer"), followed by the [tutorial](../tutorial-prov/) and then [PROV-O](http://www.w3.org/TR/prov-o/) for LinkedData/RDF/OWL (alternatively [PROV-XML](http://www.w3.org/TR/prov-xml/) for XML or alternatively [PROV-JSON](http://provenance.ecs.soton.ac.uk/prov-json/) for JSON). For deeper understanding and definition of the PROV concepts, see the [PROV datamodel](http://www.w3.org/TR/prov-dm/).