---
title: 'Resources that change state'
date: Tue, 29 Oct 2013 15:10:42 +0000
categories:
    - Practical Provenance
tags: ['PROV', 'FAQ']
aliases:
    -  /2022/prov/2013/10/29/resources-that-change-state/
---

The [PROV](http://www.w3.org/TR/prov-overview/ "PROV overview") working group received a question from Mike:

> My understanding is that an entity referenced in a PROV [bundle](http://www.w3.org/TR/prov-dm/#component4 "bundle") (e.g. via [wasGeneratedBy](http://www.w3.org/TR/prov-dm/#term-Generation "generation")) must be in the bundle...but I do not wish to duplicate entity definitions through out my bundles. My entities are long lived and will exist in multiple bundles.   
> So lets say I have a resource for alarms which contains a list of all alarms my company monitors. If I turn off the alarm at `alarm/1`, my understanding is that in PROV a new [entity](http://www.w3.org/TR/prov-dm/#term-entity "entity") is created for the new state of `alarm/1`.   
> But in my actual data store, I don't create a new record, I just toggle a flag. So there is a disconnect between how my PROV looks and how my data looks. This is by design is my understanding.   
> So I would have a new entity in my prov for the `alarm/1` in the new state which is a specialization of `alarm/1`, yes? Ultimately, I want to display all of the provenance for `alarm/1` so I can see its history from creation to invalidation. Am I going about this the wrong way?

Here is my reply (slightly revised for this post). My examples use the [Turtle syntax](http://www.w3.org/TR/turtle/ "Turtle, Terse RDF Triple Language") and [PROV-O](http://www.w3.org/TR/prov-o/), but are also applicable to other serializations of PROV, like [PROV-XML](http://www.w3.org/TR/prov-xml/ "PROV-XML") or [PROV-JSON](http://provenance.ecs.soton.ac.uk/prov-json/). This is a very good question. I am not sure how this relates to [bundles](http://www.w3.org/TR/prov-dm/#component4 "bundles"), so I'll start with the topic of entities and then move on to specializations and finally bundles.

Entities
--------

In [PROV](http://www.w3.org/TR/prov-primer/ "PROV primer") we describe [entities](http://www.w3.org/TR/prov-dm/#term-entity "entity") as in one way or another being 'static' descriptions of things in the world. In your example, there are two apparent abstraction levels of how 'static' an alarm is. The most general [entity](http://www.w3.org/TR/prov-o/#Entity "prov:Entity") is: 

```turtle
<alarm/1> a prov:Entity, ex:Alarm ;
   prov:atLocation <customer/5> .
``` 

We here consider the alarm over its lifetime at a given customer, no matter its current status. So we can describe its installation date as its provenance using [prov:generatedAtTime](http://www.w3.org/TR/prov-o/#generatedAtTime "prov:generatedAtTime"): 

```turtle
<alarm/1> prov:generatedAtTime "1984-05-15T17:19:41Z" .
```

We can also properties that are more fluctuating and might change during the lifetime of the entity: 

```turtle
<alarm/1> ex:currentStatus "active" ;
      ex:brightness 0.80 ;
      ex:noiseLevel 0.50 .
``` 

If I retrieve the same resource later today, this might instead show: 

```turtle
<alarm/1> ex:currentStatus "disabled" ;
      ex:brightness 0.20 ;
      ex:noiseLevel 0.89 .
``` 

This is fine, there is no requirement for a `prov:Entity` to not change its attributes -- however its provenance should not change.

Specialization
--------------

Now what if we wanted to know how it changed from active to disabled, but don't really care about all the possible levels of brightness and noise it had in-between? Then it might make sense to [specialize](http://www.w3.org/TR/prov-dm/#component5 "PROV-DM: Alternate Entities") the alarm entity to what we would in common programming probably just call "alarm state". It is still describing the same alarm, but at a finer granularity and a shorter time spam: 

```turtle
<alarm/1/state/123> a prov:Entity, ex:AlarmState ;
    prov:specializationOf <alarm/1> ;
    ex:currentStatus "active" ;
    prov:generatedAtTime "2013-10-28T18:00:00Z" ;
    prov:invalidatedAtTime "2013-10-28T23:50:00Z" .

<alarm/1/state/124> a prov:Entity, ex:AlarmState ;
    prov:specializationOf <alarm/1> ;
    ex:currentStatus "disabled" ;
    prov:generatedAtTime "2013-10-28T23:50:00Z" .
```

We might specify a new subclass `ex:AlarmState` with the understanding of 'locking down' the `ex:currentStatus` field - such subclasses would allow different kind of specialization, in case you also needed a specialization like `ex:BrightnessLog`. Each state has a different [generation](http://www.w3.org/TR/prov-o/#generatedAtTime "prov:generatedAtTime") and [invalidation time](http://www.w3.org/TR/prov-o/#invalidatedAtTime "prov:invalidatedAtTime"), indicating the life span of the state. This is a continuous span, so the alarm state that was disabled last week is different from the disabled alarm state today, because the alarm was active in the mean time. 

However both of these are [specializations of](http://www.w3.org/TR/prov-o/#specializationOf "prov:specializationOf") the entity that describe the alarm regardless of status. 

![2013-10-29-entity-specializationOf](2013-10-29-entity-specializationof.png)  
[[powerpoint source](2013-10-29-entity-specializationOf.pptx)]

You might want to organize these states in an order so you don't need to compare the start/end timestamps, using [prov:wasRevisionOf](http://www.w3.org/TR/prov-o/#wasRevisionOf "prov:wasRevisionOf"). 

```turtle
<alarm/1/state/124> prov:wasRevisionOf <alarm/1/state/123> .
<alarm/1/state/123> prov:wasRevisionOf <alarm/1/state/122> .
```

So what if we want to describe who disabled it? A simple solution is to now just provide [prov:wasAttributedTo](http://www.w3.org/TR/prov-o/#wasAttributedTo "prov:wasAttributedTo") at each state -- (indicating who was associated with the activity that led to its creation): 

```turtle
<alarm/1/state/124> prov:wasAttributedTo <customer/5>.
```

So now we know that `customer/5` caused the alarm to be disabled somehow (it was probably not a corrupt supervisor at the security company). If you want to detail this more, say to record how the customer did this (e.g. clicking the alarm panel) - then you can introduce an [activity](http://www.w3.org/TR/prov-o/#Activity "prov:Activity") to describe the transition: 

```turtle
<alarm/1/state/123> prov:wasInvalidatedBy <activities/987> ;
<alarm/1/state/124> prov:wasGeneratedBy <activities/987> .

<activities/987> a prov:Activity, ex:AlarmPanelAction ;
    prov:wasAssociatedWith <customer/5> .
```

Bundles
-------

Now as to get back to the bundles - a [prov:Bundle](http://www.w3.org/TR/prov-o/#Bundle "prov:Bundle") is defined as

> a named set of provenance descriptions, and is itself an Entity, so allowing provenance of provenance to be expressed

Now I would say that any resource that contains provenance statements (and in particular PROV statements) is a prov:Bundle. However this fact and typing might not be recorded anywhere, and it would generally only be used as a term when you want to describe provenance of provenance records, or if you are cataloguing provenance traces. So moving to your example, perhaps the provenance of the longer-living entities (the alarm and their installations) are recorded in a separate resource, e.g. `alarm/all`; while you record short-lived alarm states in a different resource, e.g. `events/2013-10` for alarm events this month. 

Now you might not want to include the full provenance of `alarm/1` within `events/2013-10` - and so you can use [prov:mentionOf](http://www.w3.org/TR/prov-links/ "PROV: Linking Across Provenance Bundles") and `prov:asInBundle` to indicate that you are specializing an entity that is described in a different bundle. 

```turtle
<alarm/1/state/124> prov:mentionOf <alarm/1> ;
  prov:asInBundle <http://example.com/alarms> .
``` 

In a way this is just a more formal way of saying: 

```turtle
<alarm/1/state/124> prov:specializationOf <alarm/1> .
<alarm/1> prov:has_provenance <http://example.com/alarms> .
```

Above we used [prov:has\_provenance](http://www.w3.org/TR/prov-aq/ "PROV-AQ: Provenance Access and Query"), which is a looser way to say that you should be able to find a provenance description in the given resource that somewhat involves the resource. Using prov:mentionOf and prov:asInBundle adds the additional meaning that you mean to specialize the entity _as it is described in that bundle_. 

This might not always be what you want, the exact interpretation of this is still application specific, for instance above we don't intend for the current `ex:currentStatus` to be inherited by the different timestamped states, but the `prov:atLocation` of `alarm/1` is also true for both `alarm/1/state/123` and `alarm/1/state/124`.

Conclusion
----------

As in any kind of modelling, consideration needs to taken as to what granularity of description is beneficial for each particular use case. Entities provides a way to describe a resource with some aspects frozen, enabling us to describe its provenance. For instance, an alarm can be described as a series of alarm states, which each a certain time period they exist over. It is however domain-specific what we mean is included in the snapshot and what is considered just additional properties. PROV specialization allow us to relate entities that are descriptions of the same _thing in the world_, but at different abstraction levels, for instance covering different time spans.

# Comments

#### 
[lucmoreau](http://lucmoreau.wordpress.com "l.moreau@ecs.soton.ac.uk") - <time datetime="2013-10-29 15:52:02">Oct 2, 2013</time>

Hi Stian, I like the way you developed this example. Something that the working group has never fully discussed is how we can determine which properties can be fluctuating for an entity, and which have been frozen. In your example, how can a third-party decide whether ex:currentStatus "active" is or is not a fixed attribute-value for an entity? Any thoughts on this?
<hr />

#### 
[soilandreyes](http://soiland-reyes.com/stian/work/ "soiland-reyes@cs.manchester.ac.uk") - <time datetime="2013-10-29 17:16:37">Oct 2, 2013</time>

That is a good question. For other readers: Initially in the working group we had the idea that _all properties_ on an entity was in "snapshot". However we relaxed this requirement as it meant you were forced to always mint a new URI for the Entity to describe a Resource (which might already have other, mutable properties), and we would rather have the ability for the Entity to normally have the same URI as the resource. 

Specializations should thus be needed only when you really need several abstraction levels. But the question then becomes as how you can know of what is "in flux" and what is a more permanent record that is a true property for the resource over its entire lifetime. One way to do this is to just say so in the ontology of a class that you assign to the entity. 

This could even be programmatic, so in owl, if we have `:Professor` which is a subclass of `prov:Person` - this could be used as a `prov:specializationOf` for a person as they have not been professors their whole life. In OWL we can require that professors have the property restriction `prov:actedOnBehalfOf exact 1 schema:University` -- this would require such a relation to exist in order to be a Professor and could be said to be "locked down". 

However, as OWL nor RDF deals with resource changes over time - this does not mean that the resource has always been a Professor or that the professor was always working at the same university. Perhaps a more formal solution would be a way to specify this immutability as a similar statement for a given class/type of entities.
<hr />
