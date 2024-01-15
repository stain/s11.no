---
title: "Conclusions"
weight: 62
lang: en-GB
categories:
  - PhD
summary: > 
  Conclusions for the research questions raised in introduction.
---

From research question [RQ1](../../../2022/phd/introduction/#rq1) I asked if the FAIR Digital Object (FDO) concept was realisable using existing Web technology, which was explored by [chapter 2](../../../2023/phd/background/) and [chapter 3](../../../2023/phd/fdo-and-linked-data/) and discussed in [section 6.1](../discussion/).
The conclusion is that Web approaches can practically achieve FDO goals, by combining existing standards in a normated way.
However FAIR practitioners cannot simply equate Semantic Web with FDO, but need to also ensure sufficient constraints to guarantee navigational machine-actionability, balanced against developer usability and extensibility. 

For research question [RQ2](../../../2022/phd/introduction/#rq2)  I endevour further on the challenge mentioned above: [Chapter 4](../../../2023/phd/ro-crate/) introduced _RO-Crate_ as such a pragmatic and normative approach that has been implemented by multiple open source developers for a wide range of applications.
As discussed in section [section 6.1](../discussion/), to build a reliable and extensible FDO ecosystem, the lightweight recommendations of RO-Crate needs to be combined with community-developed profiles which provide validation and tailored user interfaces.

In answer to the final research question [RQ3](../../../2022/phd/introduction/#rq3), [chapter 5](../../../2023/phd/workflows/) covered different aspects, by proposing research software wrapped as canonical workflow building blocks, incrementally building FDOs from a workflow system, and recording workflow execution provenance.
All of these have in common that they are implemented using RO-Crate and compatible with the other approaches from chapter 4, e.g. for visualisation and editing.
For workflow provenance, [section 5.4](../workflow-run-crate/) introduced the Workflow Run Crate profiles (WRROC).
These were implemented by six different workflow systems, with maturing tooling and practical use cases that showcase how different developers (many not familiar with Semantic Web technologies) can adopt an interoperable approach to FDOs using pragmatic guidance to Linked Data.