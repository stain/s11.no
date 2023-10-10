---
title: PROV-N Cheat Sheet
date: 2023-10-10
categories:
    - Practical Provenance
tags: ['PROV', 'prov-n']
summary: This is a quick "cheat sheet" for the PROV-N syntax.
---

This is a quick "cheat sheet" for the PROV-N syntax. 

See also the [PROV-N specification](https://www.w3.org/TR/prov-n/), [PROV Primer](https://www.w3.org/TR/prov-primer/) and the blog post [Validating and visualising PROV](../validating-and-visualising-prov/).


```prolog
document

  /* prefix prov <http://www.w3.org/ns/prov#> */
  prefix ex <http://example.com/>
  prefix s <http://schema.org/>

  entity(ex:entity1)
  entity(ex:entity2, [prov:label="Second entity",
                      prov:type='s:ScholarlyArticle',
                      s:description="A long example"])
  entity(ex:plan1, [prov:type='prov:Plan',
                    prov:value="Do all the work"])
  
  agent(ex:agent1)
  agent(ex:agent2, [prov:label="Alice W. Land",
                    prov:type='prov:Person'])
  
  /* or prov:SoftwareAgent, prov:Organization  */
  
  activity(ex:activity1)
  activity(ex:activity2, [prov:label="Making it"])
  
  wasStartedBy(ex:activity1, -, -, 2023-11-16T15:00:00)
  wasStartedBy(ex:activity2, ex:triggerEntity,
               ex:startingActivity1, 2023-11-16T16:00:00)
  
  wasEndedBy(ex:activity1, -, -, 2023-11-16T17:30:00)
  wasEndedBy(ex:activity2, ex:triggerEntity, ex:activity1,
             2023-11-16T17:00:00)
  
  used(ex:activity1, ex:entity1, -)
  used(ex:activity1, ex:entity1, 2023-03-02T10:30:00,
       [prov:role='ex:someRole'])
  
  wasGeneratedBy(ex:entity2, ex:activity1, -)
  wasGeneratedBy(ex:entity2, ex:activity1, 2023-03-02T17:00:00)
  
  wasAssociatedWith(ex:activity1, ex:agent1, -)
  wasAssociatedWith(ex:activity2, ex:agent2, ex:plan1)
  
  actedOnBehalfOf(ex:delegateAgent2, ex:responsibleAgent1)
  actedOnBehalfOf(ex:delegateAgent2, ex:responsibleAgent1,
                  ex:activity1, [prov:label="supervised by"])
  
  wasAttributedTo(ex:entity1, ex:agent1)
  
  wasDerivedFrom(ex:newEntity, ex:basedOnEntity)
  wasDerivedFrom(ex:dataset2, ex:dataset1,
                 [prov:type='prov:Revision'])
  /* or prov:Quotation, prov:PrimarySource  */
  
  wasInfluencedBy(ex:entity1, ex:entity2)
  
  specializationOf(ex:entity1v1, ex:entity1)
  alternateOf(ex:entity1v2, ex:entity1v1)

endDocument
```

Note: Some of the relations require `-` placeholders, e.g. `used()`, while they are optional in others.
