---
title: "Supplement 99: Recording provenance of workflow runs with RO-Crate"
weight: 9999
lang: en-GB
categories:
  - PhD
keywords:
  - workflow
  - provenance
  - RO-Crate
summary: > 
  Working Document
description: > 
    Recording the provenance of scientific computation results is fundamental to support traceability, reproducibility and quality assessment of data products. Several models have been explored to address this need, providing representations of workflow plans and their executions as well as means of packaging the resulting information for archiving and sharing. However, they lack interoperability, flexibility and support from workflow management systems. In this work we present Workflow Run RO-Crate, an extension of RO-Crate (Research Object Crate) to capture the provenance of the execution of computational workflows at different levels of granularity. We describe the model, as well as its implementations in workflow systems, and show its applicability to machine learning for digital pathology use cases. The model is developed by a diverse, open community that runs regular meetings, discussing requirements and practical aspects. The format is already in use in several workflow managers, including Galaxy, allowing interoperable comparisons between runs from heterogeneous systems.
---

<h2>Cite as</h2>

Simone Leo, Michael R. Crusoe, Laura Rodríguez-Navas, Raül Sirvent, Alexander Kanitz, Paul De Geest, Rudolf Wittner, Luca Pireddu, Daniel Garijo, José M. Fernández, Iacopo Colonnelli, Matej Gallo, Tazro Ohta, Hirotaka Suetake, Salvador Capella-Gutierrez, Renske de Wit, Bruno de Paula Kinoshita, Stian Soiland-Reyes (2023):  
**Recording provenance of workflow runs with RO-Crate**.  
_In preparation_  

* **License**: Creative Commons Attribution License ([CC BY 4.0](https://spdx.org/licenses/CC-BY-4.0)). 
* **Modifications**: Formatting as Markdown, abstract only


# Recording provenance of workflow runs with RO-Crate

_Simone Leo<sup>1</sup>, Michael R. Crusoe<sup>2,3,4</sup>, Laura Rodríguez-Navas<sup>5</sup>, Raül Sirvent<sup>5</sup>, Alexander Kanitz<sup>6,7</sup>, Paul De Geest<sup>8</sup>, Rudolf Wittner<sup>9,10,11</sup>, Luca Pireddu<sup>1</sup>, Daniel Garijo<sup>12</sup>, José M. Fernández<sup>5</sup>, Iacopo Colonnelli<sup>13</sup>, Matej Gallo<sup>9</sup>, Tazro Ohta<sup>14,15</sup>, Hirotaka Suetake<sup>16</sup>, Salvador Capella-Gutierrez<sup>5</sup>, Renske de Wit<sup>2</sup>, Bruno de Paula Kinoshita<sup>5</sup>, Stian Soiland-Reyes<sup>17,18</sup>_

<div class="affiliations">

<sup>1</sup> Center for Advanced Studies, Research, and Development in Sardinia (CRS4), Loc. Piscina Manna, Edificio 1, 09050 Pula (CA), Italy\
<sup>2</sup> Vrije Universiteit Amsterdam, The Netherlands\
<sup>3</sup> DTL Projects, The Netherlands\
<sup>4</sup> Forschungszentrum Jülich, Germany\
<sup>5</sup> Barcelona Supercomputing Center (Spain)\
<sup>6</sup> Biozentrum, University of Basel, Switzerland\
<sup>7</sup> Swiss Institute of Bioinformatics, Lausanne, Switzerland\
<sup>8</sup> VIB-UGent Center for Plant Systems Biology, Gent, Belgium\
<sup>9</sup> Faculty of Informatics, Masaryk University, Botanická 68a, 602 00, Brno, Czech Republic\
<sup>10</sup> Institute of Computer Science, Masaryk University, Šumavská 416/15, 602 00, Brno, Czech Republic\
<sup>11</sup> BBMRI-ERIC, Neue Stiftingtalstrasse 2, 8010, Graz, Austria\
<sup>12</sup> Ontology Engineering Group, Universidad Politécnica de Madrid\
<sup>13</sup> Università degli Studi di Torino, Computer Science Dept. Corso Svizzera 185, 10149, Torino, Italy\
<sup>14</sup> Database Center for Life Science, Joint Support-Center for Data Science Research, Research Organization of Information and Systems, Shizuoka, Japan\
<sup>15</sup> Institute for Advanced Academic Research, Chiba University, Chiba, Japan"\
<sup>16</sup> Department of Creative Informatics, Graduate School of Information Science and Technology, The University of Tokyo, Tokyo, Japan\
<sup>17</sup> Department of Computer Science, The University of Manchester, Manchester, United Kingdom \
<sup>18</sup> Informatics Institute, Faculty of Science, University of Amsterdam, Amsterdam, The Netherlands

</div>



## Abstract

Recording the provenance of scientific computation results is fundamental to support traceability, reproducibility and quality assessment of data products. Several models have been explored to address this need, providing representations of workflow plans and their executions as well as means of packaging the resulting information for archiving and sharing. However, they lack interoperability, flexibility and support from workflow management systems. In this work we present Workflow Run RO-Crate, an extension of RO-Crate (Research Object Crate) to capture the provenance of the execution of computational workflows at different levels of granularity. We describe the model, as well as its implementations in workflow systems, and show its applicability to machine learning for digital pathology use cases. The model is developed by a diverse, open community that runs regular meetings, discussing requirements and practical aspects. The format is already in use in several workflow managers, including Galaxy, allowing interoperable comparisons between runs from heterogeneous systems.

## (Work in progress)

_This manuscript is under development and will be published as a preprint once submitted._


