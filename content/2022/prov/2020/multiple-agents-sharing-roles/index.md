---
title: 'Multiple agents sharing roles'
date: Tue, 01 Dec 2020 15:03:48 +0000
draft: false
tags: ['Uncategorized']
---

Assuming the task of writing provenance for a student group exercise, consider the question:

> Do we need to assign everyone in the group a specific role since in our group we found that for many of the tasks, everyone worked together to complete it?
> 
> MSc Student in Understanding Data and their Environment, University of Manchester, 2020

This blog post explores the different PROV patterns that could describe this scenario.

If you all worked together without distinguishing roles, then you can either assign the same role to each agent (showing you shared that role) or not have any roles.

```
prefix ex [http://example.com/](http://example.com/)
prefix terms [http://example.com/terms#](http://example.com/terms#)
agent(ex:Alice)
agent(ex:Bob)
activity(ex:writingCards, [prov:type='terms:CardWriting'])
wasAssociatedWith(ex:Alice, ex:writingCards,
                  [prov:role='terms:Writing'])
wasAssociatedWith(ex:Bob, ex:writingCards,
                  [prov:role='terms:Writing'])
```

While the role `terms:Writing` above does not really tell us much as the activity is already of type `terms:CardWriting`, the distinction is somewhat that not saying the role is "_We don't know / didn't say what work they did_" while explicit role is saying "_They did the same work, but we have not broken it down further_".

In a way a role is a short-circuiting device to avoid having infinite recursion into very tiny activities – it allows multiple things to happen in the same activity.

Let's say Charlie helped with putting addresses on the envelopes, in our simple one-activity modelling we can associate them with a separate role:

Now we know who to blame if the cards end up on the North pole!

It is a modelling question to use a single activity with multiple agents associated, potentially with different roles; or to use multiple activities with simpler associations, perhaps not needing roles. One thing to keep in mind is that more activities will also need more entities to represent the different states, e.g. `ex:unwrittenCard1`, `ex:writtenCard1`, `ex:addressedCard1`.

Groups
------

Rather than associating multiple agents to a single activity it is possible to make a new agent that represent the whole group, in which case it is a choice to not break down to individual engagement.

For instance this would be correct if recording a board room decision, where the group of Alice, Bob and Charlie together decided/stated something they may agreed with or be responsible for individually.

PROV does not itself define how to specify the make-up of groups – but  
it has [agent types](https://www.w3.org/TR/2013/REC-prov-dm-20130430/#concept-organization) `prov:Person`, `prov:Organization` and  
`prov:SoftwareAgent` that you can assign using `prov:type`.

A student group might not sound like an _organization_, but it is the  
closest match of the three. We also see that there is an equivalent type [Organization](http://schema.org/Organization) in the schema.org vocabulary, with looser sub-types including [PerformingGroup](https://schema.org/PerformingGroup) (a band or orchestra), [Project](http://schema.org/Project) (someone working towards a shared goal) or even [CollegeOrUniversity](http://schema.org/CollegeOrUniversity) (the University as a whole).

While PROV literature does not cover well how to use external vocabularies like schema.org, we can take advantage of such types and attributes in PROV-N and express group membership using [schema.org/member](http://schema.org/member), adding a [parentOrganization](http://schema.org/parentOrganization) relation to the University for good measure.

```
prefix s <http://schema.org/> 
```

The keen reader will notice that the above example repeats some attribute names to express multiple relations of `prov:type` and `s:member` – both of these are _unordered_.

Collections
-----------

As an alternative, PROV has the concept of [Collections](https://www.w3.org/TR/prov-dm/#component6).

Although collections are mainly used for describing compound entities, such as a dataset containing samples, as _agents can concurrently be entities_  
they could also be used for showing group members.

**Tip:** Treating a agent as an entity can be of interest if your provenance need to show its evolution over time, for instance changes to group membership. In this case, note that you will need multiple agent identifiers depending on which "version" of the group was associated with particular activities across time, or use [specialization](https://www.w3.org/TR/prov-primer/#alternate-entities-and-specialization-1) to make a "timeless" entity.

Using `prov:Collection` would perhaps feel more PROV native than schema.org use above, but without any additional attributes like `parentOrganization`:

This choice between vocabularies is I'm afraid part of **data modelling** — there will never be a single perfect metadata model, and so we have to either pick the one that is most useful, or find a way to combine both approaches. (Although verbose, the above should work both ways)

Sometimes two metadata models can be in conflict in terms of granularity, in which case you should use different identifiers, in some cases even different documents.