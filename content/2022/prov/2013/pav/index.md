---
title: 'Recording authorship, curation and digital creation with the PAV ontology'
date: Thu, 28 Mar 2013 12:12:55 +0000
draft: false
tags: ['Vocabularies']
---

[PAV](https://code.google.com/p/pav-ontology/wiki/Homepage "PAV homepage") is a lightweight ontology for tracking _Provenance, Authoring and Versioning_. PAV supplies terms for distinguishing between the different roles of the agents contributing content in current web based systems: _contributors_, _authors_, _curators_ and digital artifact _creators_. The ontology also provides terms for tracking provenance of digital entities that are published on the web and then _accessed_, _transformed_ and _consumed_. [PAV version 2.1.1 was released on 2013-03-27](https://code.google.com/p/pav-ontology/wiki/Versions#PAV_ontology_v2.1.1_(2013-03-26)), making PAV an extension of the W3C provenance ontology [PROV-O](http://www.w3.org/TR/prov-o/), thus  enabling interoperability between PAV and PROV-compliant tools such as [ProvToolbox](https://github.com/lucmoreau/ProvToolbox).

Overview
--------

[![pav-simpler](http://practicalprovenance.files.wordpress.com/2013/03/pav-simpler1.png)](http://practicalprovenance.files.wordpress.com/2013/03/pav-simpler1.png) _Note: PAV does not define any classes, and the PAV properties do not put any explicit restrictions on their domain/ranges. Therefore the classes above, like "another resource", are only for illustration of typical use. The diagram above does not show data properties attached to resources, like pav:createdOn._

Example
-------

Here's an example of using PAV: https://gist.github.com/stain/5262169 This example shows how the blog post `http://example.com/blog.html` was [createdBy](http://purl.org/pav/html#http://purl.org/pav/createdBy) Alice. The blog post was [createdWith](http://purl.org/pav/html#http://purl.org/pav/createdWith) the software Wordpress. The content of the blog was [importedFrom](http://purl.org/pav/html#http://purl.org/pav/importedFrom) `http://example.com/data.csv` (presumably a CSV file), and this was [importedBy](http://purl.org/pav/html#http://purl.org/pav/importedBy) the script csv2html. Although Alice is the _creator_ (as she made the blog post), `http://example.com/blog.html` is [authoredBy](http://purl.org/pav/html#http://purl.org/pav/authoredBy) Bob, he made the original data and therefore also is the _author_ of (the content of) the blog post. The post was [curatedBy](http://purl.org/pav/html#http://purl.org/pav/curatedBy) Charlie, who perhaps edited the CSV (or HTML) to include the correct column headers. We also notice that the blog was [importedOn](http://purl.org/pav/html#http://purl.org/pav/importedOn) March 2013, while the content was [authoredOn](http://purl.org/pav/html#http://purl.org/pav/authoredOn) December 2012. We don't know when Charlie curated it, although this could have been provided with [curatedOn](http://purl.org/pav/html#http://purl.org/pav/curatedOn) Additional PAV properties allows specifying attributions like [contributors](http://purl.org/pav/html#http://purl.org/pav/contributedBy), the [provider](http://purl.org/pav/html#http://purl.org/pav/providedBy) in addition to other kind of sources, such as [direct downloading](http://purl.org/pav/html#http://purl.org/pav/retrievedFrom), [verification against source material](http://purl.org/pav/html#http://purl.org/pav/sourceAccessedAt) and [derivation](http://purl.org/pav/html#http://purl.org/pav/derivedFrom) when further refinements have been made. Data can be given a [version](http://purl.org/pav/html#http://purl.org/pav/version) number, indicate its lineage to a [previous version](http://purl.org/pav/html#http://purl.org/pav/previousVersion), and indicate when a source was [last updated](http://purl.org/pav/html#http://purl.org/pav/lastUpdatedOn).

The PAV approach
----------------

The goal of PAV is to provide a lightweight, straight forward way to give the essential information about _authorship_, _provenance_ and _versioning_, and therefore these properties are described directly on the published resource. As such, PAV does not define any classes or restrict domain/ranges, as all properties are applicable to any online resource. This "flat" approach mean that it is easy to use and query PAV without a deep understanding of provenance models, but at a small cost that more complex relationships are not expressed. For instance, pav:authoredBy allows multiple authors, but if there are multiple authors we won't know who wrote what; or when they did so. Such details can be included alongside PAV using other PROV statements.

Combining PAV with other PROV extensions
----------------------------------------

Here's an example combining PAV with another PROV extension, the [Provenance Vocabulary](http://trdf.sourceforge.net/provenance/ns.html). https://gist.github.com/stain/5262532 This example shows how `http://example.com/data.csv` was downloaded from `http://example.org/originalData` with HTTP 1.1 and requesting `Accept: text/csv` by content negotiation. The PAV term `pav:retrievedFrom` gives the short-cut to the original data, while `prv:retrievedBy` gives details of the transport and content-negotiation used in the download. By combining vocabularies in such an approach it is possible to query the provenance for PAV statements in order to get a general overview of the provenance, and then explore other PROV statements for more specific details, which structure might not be known in advance.

Using PAV
---------

To use PAV, import the [PAV ontology](http://purl.org/pav/) from the namespace http://purl.org/pav/ and read the [PAV documentation](http://purl.org/pav/html). The [PAV wiki pages](https://code.google.com/p/pav-ontology/wiki/Homepage) contain details about the [PAV versions](https://code.google.com/p/pav-ontology/wiki/Versions). If your ontology extends or uses PAV, you can use either:```
owl:imports <http://purl.org/pav/>
```for the latest version (which might at some point include additional properties), or```
owl:imports <http://purl.org/pav/2.1>
```for the latest patch version of 2.1 (ie. no new terms will be added later).

Extracting PROV-O statements
----------------------------

As PAV is meant as a lightweight ontology, the inferred PROV-O statements are not usually explicitly included. Any OWL or RDFS reasoner should be able to infer the PROV-O statements as long as the PAV ontology is imported from http://purl.org/pav/ As an example of PAV interoperability with PROV, we built a [Taverna workflow](http://www.myexperiment.org/workflows/3424 "Visualize PAV provenance as SVG") which uses the [OWL reasoner Pellet](http://clarkparsia.com/pellet/) to infer PROV statements, and then visualize this as SVG using the [PROV toolbox](https://github.com/lucmoreau/ProvToolbox). Here's the diagram (as PNG) visualizing the [PAV example](https://gist.github.com/stain/5262169) from the beginning of this page: [![pav-example](http://practicalprovenance.files.wordpress.com/2013/03/pav-example.png?w=625)](http://practicalprovenance.files.wordpress.com/2013/03/pav-example.png)