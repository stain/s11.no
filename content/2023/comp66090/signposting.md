---
title: Building knowledge graphs using FAIR Signposting on the Web
date: 2023-11-20
summary: > 
  Follow HTTP Link headers to retrieve and combine Linked Data in a triple-store.
---

_COMP66090 MSc project 2023/2024_

* [COMP66090 Handbook entry](https://studentnet.cs.manchester.ac.uk/pgt/2023/COMP66090/project/projectbookdetails.php?projectid=54256)
* This project has PhD potential
* Skills needed: Logic, IT management

## Background

Linked Data is used to publish structured metadata and machine-actionable descriptions on the Web (see [COMP62342](http://syllabus.cs.manchester.ac.uk/pgt/2021/COMP62342/slides/Week5-LinkedDataRDF.pdf)). This is an important ingredient for making research data [FAIR](https://www.go-fair.org/fair-principles/): Findable, Accessible, Interoperable and Reusable. However, there is often a divergence between the Semantic Web representations and human-readable Web representations, for instance on identifiers, types and overall resource navigation.

This means there can be a significant barrier from traditional Web crawls to access the corresponding FAIR elements as Linked Data. Even if Linked Data use the URLs as core identifier type, it is often unclear what will be possible for a machine to retrieve from that URL. Linked Data may also be using many different vocabularies, e.g. DCAT3 vs schema.org.

[Signposting](https://signposting.org/) is a simple approach to mitigate this, using existing Web standards to make navigational links expicit for machine consumption. Existing Linked Data tooling such as RDF libraries however have limited, if any, support for Web crawling or navigation through such signposting, and rely on explicit programmatic loading of data sources. This means that the machine-readable Web largely still requires human interaction, and that FAIR consumption tools can give inconsistent results.

## Description

You will explore and describe current technologies for Linked Data and Signposting, and identify how they can be tighter integrated to further automate machine-actionability of Linked Data resources with FAIR Signposting. You will plan and prototype a tool or service that can incrementally follow Signposting to retrieve associated Linked Data, then selectively load these into a joint knowledge graph (e.g. Apache Jena Fuseki). You will explore existing open source technologies and libraries for your chosen programming language.

Following the building of the knowledge graph you can then execute explorative queries on the Linked Data, and decide on which resources to next follow signposting for, allowing for heuristic fallbacks for when no Signposting is available. It is crucial that the software includes sufficient logic for determining when to stop the crawl and how to select resources of interest. This crawling of FAIR resources on the Web can build a completed single dataset of the graph, which can be deposited in public repositories with associated provenance.

Possible additional explorations includes nested objects such as Research Objects, inclusion of linked data embedded in HTML (e.g. schema.org), FAIR evaluation, building Signposting testing benchmarks and a more theoretical comparison with FAIR Digital Object (FDO) requirements.


## References

* <https://jena.apache.org/documentation/fuseki2/>
* <https://faircookbook.elixir-europe.org/>
* <https://signposting.org/FAIR/>
* <https://www.go-fair.org/fair-principles/>
* <https://pypi.org/project/signposting/>