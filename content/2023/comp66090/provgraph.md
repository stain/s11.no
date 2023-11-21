---
title: Interactive Web application for constructing provenance graphs
date: 2023-11-20
summary: > 
  Develop a web-based GUI for making PROV.
---

_COMP66090 MSc project 2023/2024_

* [COMP66090 Handbook entry](https://studentnet.cs.manchester.ac.uk/pgt/2023/COMP66090/project/projectbookdetails.php?projectid=54247)
* Skills needed: Logic, Programming

## Background

[PROV](https://www.w3.org/TR/prov-overview/) is a W3C Web standard and model for representating provenance graphs, for instance for describing how a dataset was derived from original sources and processed by humans and software. The core of PROV are the three object types entity, activity and agent which are then interrelated to form a provenance trace.  At the University of Manchester we [use PROV](https://s11.no/2022/prov/) as part of Data Science teaching, as well as in large European research projects.

There are several software tools that can work with PROV documents, including the [PROV Store](https://openprovenance.org/store/) which can do [visualizations](https://s11.no/2020/prov/validating-and-visualising-prov/).  PROV can be written in different textual file formats, either by hand, or using software libraries like the [prov Python package](https://pypi.org/project/prov/) or the [PROV Toolbox for Java](https://lucmoreau.github.io/ProvToolbox/). It is also possible to convert PROV to [ontology-based](https://www.w3.org/TR/prov-o/) Linked Data. However, no friendly user interface exists that could allow creation of PROV without editing source code.

## Description

This project will develop a Web application that allow step-by-step building of a PROV graph. You will learn the core PROV concepts (using our Data Science teaching material) and then help decide what user interface would be sensible for generating a basic provenance graph.

For instance it can be diagram-based with drag-and-drop (e.g. using existing Javascript diagram libraries and SVG), or it could be form-based where the user can connect the different PROV elements (e.g. using AngularJS). The end result should be a PROV document in one of the formats compatible with the existing PROV tools, for instance for generating a PROV diagram.

You will make a plan for implementing such an application and decide on its storage model. You should investigate existing open source libraries that can help you implement the software, which should also inform your choice of programming languages and the overall architecture (for instance client-server or Web apps).

Finally you will start prototyping the application in your preferred programming language. We will guide you on following open source best practices and will assist in deploying the live application.

Depending on your preferences and background, there is room for alternatively exploring further topics related to provenance, for instance graph theory, linked data or information modelling. This can be suitable for a more theoretical approach than pure software engineering.

## Deliverables
	
* Architecture overview
* Implementation and testing plan
* Evaluation of existing technologies
* Prototype of application
* Integration testing
* Source code (we encourage making open source)

## References

1. <https://openprovenance.org/store/>
2. <https://www.w3.org/TR/prov-primer/>
3. <https://s11.no/2020/prov/validating-and-visualising-prov/>