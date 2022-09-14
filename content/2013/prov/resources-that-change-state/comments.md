---
title: 'Resources that change state'
date: Tue, 29 Oct 2013 15:10:42 +0000
draft: false
tags: ['PROV']
---


#### 
[lucmoreau](http://lucmoreau.wordpress.com "l.moreau@ecs.soton.ac.uk") - <time datetime="2013-10-29 15:52:02">Oct 2, 2013</time>

Hi Stian, I like the way you developed this example. Something that the working group has never fully discussed is how we can determine which properties can be fluctuating for an entity, and which have been frozen. In your example, how can a third-party decide whether ex:currentStatus "active" is or is not a fixed attribute-value for an entity? Any thoughts on this?
<hr />
#### 
[soilandreyes](http://soiland-reyes.com/stian/work/ "soiland-reyes@cs.manchester.ac.uk") - <time datetime="2013-10-29 17:16:37">Oct 2, 2013</time>

That is a good question. For other readers: Initially in the working group we had the idea that _all properties_ on an entity was in "snapshot". However we relaxed this requirement as it meant you were forced to always mint a new URI for the Entity to describe a Resource (which might already have other, mutable properties), and we would rather have the ability for the Entity to normally have the same URI as the resource. Specializations should thus be needed only when you really need several abstraction levels. But the question then becomes as how you can know of what is "in flux" and what is a more permanent record that is a true property for the resource over its entire lifetime. One way to do this is to just say so in the ontology of a class that you assign to the entity. This could even be programmatic, so in owl, if we have `:Professor` which is a subclass of `prov:Person` - this could be used as a `prov:specializationOf` for a person as they have not been professors their whole life. In OWL we can require that professors have the property restriction "prov:actedOnBehalfOf exact 1 schema:University" - this would require such a relation to exist in order to be a Professor and could be said to be "locked down". However, as OWL nor RDF deals with resource changes over time - this does not mean that the resource has always been a Professor or that the professor was always working at the same university. Perhaps a more formal solution would be a way to specify this immutability as a similar statement for a given class/type of entities.
<hr />
