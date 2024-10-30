---
title: Validating semantic artefact profiles for Research Object Crates
date: 2023-11-20
summary: > 
  Develop a profile-based validator using Linked Data technologies (ShEx, SHACL)
---

_COMP66090 MSc project 2024/2025_

* [COMP66090 Handbook entry](https://studentnet.cs.manchester.ac.uk/pgt/2023/COMP66090/project/projectbookdetails.php?projectid=56728)
* Skills needed: Logic, Programming

## Background

Research Object Crate ([RO-Crate](https://w3id.org/ro/crate)) is a community-based specification for sharing complex research data with structured metadata on the Web. 
It is based on existing Linked Data standards and the [schema.org vocabulary](https://schema.org/) favoured by Google, Microsoft Bing and other search engines for Rich Web Results and integration with knowledge graph tecnhologies.

RO-Crate defines a core profile of specific requirements for a JSON-LD file, that gives consistent representations for largely bibliographic metadata for the data, but can also detail provenance and software executions and open-ended extensions using Linked Data. 
Different research domains and infrastructures expand these requirements to provide [more specific profiles](https://www.researchobject.org/ro-crate/profiles.html), for instance for biodiversity data (species, geolocation), cultural heritage (natural language recordings) or additional computational details (Jupyter notebooks, Docker containers). 
Interactive tools like [Crate-O](https://language-research-technology.github.io/crate-o/) use such profiles to dynamically build a customized user interface, as well as providing rudimentary validation.

Validation is an important pre-requisite before reliable programmatic consumption of any data, particularly from the Web. 
As RO-Crate is based on Linked Data standards (RDF and JSON-LD), several mature technologies exist that can be used for a thorough and flexible validation, including JSON Schema, RDF shapes (ShEX, SHACL) and query languages (SPARQL, JQ).

## Description

In this project you will refresh background on Linked Data technology in order to investigate the existing RO-Crate [Profile Crate formalization](https://www.researchobject.org/ro-crate/1.2-DRAFT/profiles) (based on [W3C Profiles vocabulary](https://www.w3.org/TR/dx-prof/)). 
You'll decide on (and justify) which existing technologies should be combined in order to provide a flexible profile-based validation of existing RO-Crates.

You'll develop or extend an open source validator tool/service/library that uses the chosen technologies and retrieves the required schemas based on the profile specified by the RO-Crate or as specified by the user. 
Typical programming languages could be Python (e.g. to extend existing [RO-Crate validator](https://github.com/crs4/rocrate-validator/) code), but you are free to choose any other language.

Alternatively you can explore how to improve the Profile Crate formalization in JSON-LD to incorporate elements needed for validation, where you can develop at tool for generating equivalent shapes to be used with the existing validator. You may also explore the use of templates or simplified profile requirements to auto-generate initial versions of such schemas.

In this project you will be working with the international [RO-Crate community](https://www.researchobject.org/ro-crate/community.html) which is led by The University of Manchester together with The University of Queensland, Australia. The community provide exciting use cases from a range of scientific domain beyond Computer Science.

We encourage development of open source software, and will be assisting you in following best practices for research software engineering.

## References

1. <https://w3id.org/ro/crate>
2. <https://doi.org/10.3233/DS-210053>
3. <https://www.researchobject.org/ro-crate/tutorials.html>
4. <https://pypi.org/project/rocrate/>
5. <https://www.researchobject.org/ro-crate/1.2-DRAFT/profiles>
6. <https://book.validatingrdf.com/>
7. <https://www.w3.org/TR/dx-prof/>
