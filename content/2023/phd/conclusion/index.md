---
title: "Conclusions"
weight: 62
lang: en-GB
categories:
  - PhD
summary: > 
  Conclusions for the research questions raised in introduction.
---

In this thesis I examined how to implement <abbr>FAIR</abbr> Research Objects and Computational Workflows by building on and simplifying approaches from Linked Data.


From research question [RQ1](../../../2022/phd/introduction/#rq1) I asked if the FAIR Digital Object (FDO) concept was realisable using existing Web technology, which was explored by [Chapter 2](../../../2023/phd/background/) and [Chapter 3](../../../2023/phd/fdo-and-linked-data/) and discussed in [Section 6.1](../discussion/).
The conclusion is that Web approaches can practically achieve FDO goals, by combining existing standards.
However FAIR practitioners cannot simply equate Semantic Web with FDO, but need to also ensure sufficient constraints to guarantee navigational machine-actionability, balanced against developer usability and extensibility. 

For research question [RQ2](../../../2022/phd/introduction/#rq2)  I endevour further on the challenge mentioned above: [Chapter 4](../../../2023/phd/ro-crate/) introduced _RO-Crate_ as such a pragmatic and normative approach that has been implemented by multiple open source developers for a wide range of applications.
As discussed in [Section 6.1](../discussion/), to build a reliable and extensible FDO ecosystem, the lightweight recommendations of RO-Crate needs to be combined with community-developed profiles which provide validation and tailored user interfaces.
RO-Crate has been implemented by a wide range of Research Software, showing the learning curve for Linked Data can be reduced by use of common example-driven profiles and open collaborations.+

In answer to the final research question [RQ3](../../../2022/phd/introduction/#rq3), [chapter 5](../../../2023/phd/workflows/) covered different aspects, by proposing research software wrapped as canonical workflow building blocks, incrementally building FDOs from a workflow system, and recording workflow execution provenance.
All of these have in common that they are implemented using RO-Crate and compatible with the other approaches from chapter 4, e.g. for visualisation and editing.
For workflow provenance, [Section 5.4](../workflow-run-crate/) introduced the Workflow Run Crate profiles (WRROC).
These were implemented by six different workflow management systems (WfMS), with maturing tooling and practical use cases that showcase how different developers (many not familiar with Semantic Web technologies) can adopt an interoperable approach to FDOs using pragmatic guidance to Linked Data.

From the considerations of this thesis I therefore conclude that FAIR Digital Objects with computational methods can be achieved using Web-based technologies, and can be implemented by Research Software Engineers across research domains without detailed training or experience with Linked Data technologies. This is promising for realising the full potential of digitally supported research with machine-actionable reproducible scholarly outputs.
