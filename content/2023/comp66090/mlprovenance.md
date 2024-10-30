---
title: Validating semantic artefact profiles for Research Object Crates
date: 2024-10-30
summary: > 
  Develop a profile-based validator using Linked Data technologies (ShEx, SHACL)
---

_COMP66090 MSc project 2024/2025_

* [COMP66090 Handbook entry](https://studentnet.cs.manchester.ac.uk/pgt/2023/COMP66090/project/projectbookdetails.php?projectid=56802)
* Skills needed: Logic, Programming
* Type: Data on the Web, Machine learning and optimisation

## Background

Open source machine-learning models (e.g. [scikit-learn](https://scikit-learn.org/), [Tensorflow](https://www.tensorflow.org/)) have become common place for advanced statistical analysis, [large language models](https://github.com/eugeneyan/open-llms) and image recognition. Most network-based models require significant training data in order to build a set of weights that is typically tested on a subset of the data. The resulting model can be considered a mixture of data and code, as it can then be used on other "real" data e.g. for categorisation or text generation. This training is commonly done on the command line, and may require significant computational hardware resources.

[FAIR principles](https://book.the-turing-way.org/reproducible-research/rdm/rdm-fair.html) have recommendations for making datasets Findable, Accessible, Interoperable and Reusable -- in a machine-readable manner. In particular, [reproducibility](https://book.the-turing-way.org/reproducible-research/renv) is an ongoing concern for computational analysis, as changes in Platform, Research Objective, Implementation, Method, Actor or Data can all affect the program execution. For instance, changing the version of a Python library or the GPU hardware used can affect the weights of the trained model, and thus its performance and suitability.

[schema.org](https://schema.org/) is a FAIR vocabulary used on the Web for structured metadata, e.g. used by Google for their [Dataset Search](https://datasetsearch.research.google.com/). MLCommons [Croissant](https://mlcommons.org/working-groups/data/croissant/) is a profile of schema.org for describing machine learning datasets. The Research Data Aliiance has a working group for FAIR for Machine Learning ([FAIR4ML](https://archive.rd-alliance.org/groups/fair-machine-learning-fair4ml-ig)) is further developing metadata requirements for AI models.

[RO-Crate](https://www.researchobject.org/ro-crate/) is a community-based standard for packaging data with structured metadata and provenance. The [Workflow Run Crate](https://www.researchobject.org/workflow-run-crate/) profile has been used successfully with computational workflow engines to provide provenance of workflow runs. In theory can describe any combination of [command line tools processes](https://www.researchobject.org/workflow-run-crate/profiles/process_run_crate/).

The use of machine learning for analysing sensitive data (e.g. health records, census data, medical images) has great potential to improve treatments and public health, however severe security concerns have been raised about allowing a machine learning model to be trained within a *Trusted Research Environment* and still comply with the Five Safes Framework (e.g. not overfitting to leak sensitive data)*.* Detailed metadata and provenance of the training of the model, along with privacy tests, will be needed in order to build trust in the ML model not breaching privacy and to enable its publishing as a FAIR object for further reuse.

## Description

In this project you will select one or two open source ML training frameworks, and explore its current support for metadata and provenance. You will learn about the possible FAIR models to use, and experiment with modifying the ML framework to generate such structured metadata.

You may look further into post-processing to verify a ML model is reliably not overfitting or otherwise leaking sensitive data, e.g. collect statistics, testing the model with individual data points.

You may also participate in some activities of the working groups to understand and influence the state-of-the-art in FAIR Machine Learning.

## Deliverables

1. Overview of FAIR models for machine learning and current capabilities of ML frameworks  
2. Prototype modifications to ML framework(s)  
3. Autoamted post-processing analysis of ML models with corresponding provenance  
4. Example FAIR ML models published in an open repository

I encourage development of open source software, and will be assisting you in following best practices for research software engineering.

## References

* <https://doi.org/10.1145/3650203.3663326>
* <https://doi.org/10.1371/journal.pone.0309210>
* <https://doi.org/10.1088/2632-2153/ad12e3>
* <https://doi.org/10.1088/2632-2153/ad12e3>
* <https://book.the-turing-way.org/>
* <https://doi.org/10.5281/zenodo.13986378>
