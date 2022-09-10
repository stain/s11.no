---
title: 'What are good PROV-N prefixes?'
date: Tue, 01 Dec 2020 12:22:22 +0000
draft: false
tags: ['namespace', 'prefix', 'prov-n', 'Uncategorized', 'uri']
---

In this blog post we explore the role of PROV-N prefixes and how to decide on a good namespace to use your own custom provenance terms.

Most examples of PROV-N use example prefixes like:

```
prefix ex <http://example.com/>
prefix exg <http://example.org/government>
```

These [example domains](https://www.iana.org/domains/reserved) are explicitly reserved globally for all kinds of examples and training material, and deliberately do not have any content, advertisement or affiliations.

> Assume you are writing the provenance of a student group exercise, should you be using the prefix/namespace `ex` and `example.org` to define agents/entities/relationship and your own attribute types?

You **can** keep using example.org, but ideally you should define your  
own namespace based on a Web URL you "control" or "own". This would make your [Linked Data](https://www.w3.org/standards/semanticweb/data) identifiers globally unique.

Students at The University of Manchester can publish their own [home pages](https://personalpages.manchester.ac.uk/personalwebpages.html), and luckily most universities still provide a similar facility. Our students can search up themselves on [https://personalpages.manchester.ac.uk/](https://personalpages.manchester.ac.uk/) and find for instance that they are `http://personalpages.manchester.ac.uk/postgrad/alice.davidson/` which means they could make any sub-page under that directory.

Now the page does not need to exist - this blog is not about making Web pages - it is just important that it **could** exist at that address - that means it is that person's identifier space.

So we could imagine that Alice made two files under her directory:

*   `http://personalpages.manchester.ac.uk/postgrad/alice.davidson/terms`  
    Imagine this was a page defining new terms to be used in PROV
*   `http://personalpages.manchester.ac.uk/postgrad/alice.davidson/groupExercise`  
    Imagine this page was the group exercise as text (which provenance is described by PROV), or the PROV-N file itself (self-describing)

In real life you would also have to deal with file extensions like `.html` or server configuration for content types, see Tim Berners-Lee's [Cool URIs don't change](https://www.w3.org/Provider/Style/URI) for further considerations.

As above it is considered good practice to separate the prefix/namespace for new roles/attributes that you define vs specific agents/entities in one particular provenance trace. The idea being that the general terms could be reused in multiple provenance documents with the same meaning.

So let's map in the above documents as namespaces in PROV-N:

```
prefix terms <http://personalpages.manchester.ac.uk/postgrad/alice.davidson/terms#>
prefix group <http://personalpages.manchester.ac.uk/postgrad/alice.davidson/groupExercise#>
```

The prefix string usually is a short name somewhat matching the address, it just needs be unique and consistent within the same PROV document. Other documents can freely map the same namespace to a different prefix.

A diligent reader might notice the # at the end of the namespace - this "fragment" is in Web documents used to indicate a subsection or heading within the same file.

This is so that `terms:student` expands to  
`<http://personalpages.manchester.ac.uk/postgrad/alice.davidson/terms#student>`  
rather than end with `alice.davidson/termsstudent` - even if we have not made the pages now we would not want to make a separate page for each word.

In some cases separate pages are desirable, in which case the namespace  
ends in `/` to mark a directory - for instance `s:Person` becomes  
[http://schema.org/Person](http://schema.org/Person) as schema.org have decided their term list is too big to keep in a single page.

Now we can use these prefixes for identifying  
agents/entities/activities, as well as using our own attributes, roles  
and types.

```
agent(group:Alice, [prov:type='prov:Person',
                    terms:favouriteDay="Monday"])

wasAssociatedWith(group:Alice, group:studying,
                  [prov:role='terms:Reader']) 
```

It is customary that attributes start with lower `case` after `:`, while  
types/roles start with `Capital` - but this is just stylistic.

As for entity identifiers, your terms and roles should not have spaces or special characters in them as they must be combineable with the namespace to a valid URI, e.g. camel case `favouriteDay` or underscore `favourite_day`

It is possible in PROV-N (but not easily in other PROV syntaxes) to use freehand roles/types strings like `prov:role="Writing carefully"` - these are kind of anonymous and cannot be assumed to mean the same thing across multiple PROV documents.

In many cases there is no suitable URI yet, in which case using a temporary namespace like `http://example.com/yourthing` is perfectly valid as a working example, just be aware of the risk of other people having the same namespace idea!