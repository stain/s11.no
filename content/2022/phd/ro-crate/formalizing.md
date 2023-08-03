---
title: "Formalizing RO-Crate in First Order Logic"
weight: 43
bib: ro-crate
categories:
  - PhD
lang: en-GB
date-meta: '2022-01-10'
summary: > 
  Appendix from Journal article published in _Data Science_
description: > 
    Formalization of the concept of RO-Crate as a set of relations using First Order Logic
---


Below is a formalization of the concept of RO-Crate as a set of relations using First Order Logic:

### Language


Definition of language `𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊`:

```
𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊 = { Property(p), Class(c), Value(x), ℝ, 𝕊 }
     𝔻 =  𝕀𝕣𝕚
    𝕀𝕣𝕚 ≡  { IRIs as defined in RFC3987 }
     ℝ ≡  { real or integer numbers }
     𝕊 ≡  { literal strings }
```

The domain of discourse is the set of `𝕀𝕣𝕚` identifiers [[42](https://doi.org/10.17487/rfc3987)] (notation `<http://example.com/>`)[^9], with additional descriptions using numbers `ℝ` (notation `13.37`) and literal strings `𝕊` (notation `“Hello”`). 

From this formalised language `𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊` we can interpret an RO-Crate in any representation that can gather these descriptions, their properties, classes, and literal attributes.  

### Minimal RO-Crate

Below we use `𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊` to define a minimal[^8] RO-Crate:

```
                ROCrate(R) ⊨  Root(R) ∧ Mentions(R, R) ∧ hasPart(R, d) ∧ 
                               Mentions(R, d) ∧ DataEntity(d) ∧
                               Mentions(R, c) ∧ ContextualEntity(c)
               ∀r Root(r) ⇒  Dataset(r) ∧ name(r, n) ∧ 
                               description(r, d) ∧ 
                               datePublished(r, date) ∧
                               license(e, l)
          ∀e∀n name(e, n) ⇒  Value(n)
   ∀e∀s description(e, s) ⇒  Value(s)
 ∀e∀d datePublished(e, d) ⇒  Value(d)
       ∀e∀l license(e, l) ⇒  ContextualEntity(l)
             DataEntity(e) ≡  File(e) ⊕ Dataset(e)
                 Entity(e) ≡  DataEntity(e) ∨ ContextualEntity(e)
              ∀e Entity(e) ⇒ type(e, c) ∧ Class(c)
    ∀e ContextualEntity(e) ⇒ name(e, n)
            Mentions(R, s) ⊨  Relation(s, p, e)  ⊕  Attribute(s, p, l)
         Relation(s, p, o) ⊨  Entity(s) ∧ Property(p) ∧ Entity(o)
        Attribute(s, p, x) ⊨  Entity(s) ∧ Property(p) ∧ Value(x)
                  Value(x) ≡  x ∈ ℝ  ⊕  x ∈ 𝕊
```

An `ROCrate(R)` is defined as a self-described _Root Data Entity_, which describes and contains parts (_data entities_), which are further described in _contextual entities_.  These terms align with their use in the [RO-Crate 1.1 terminology](https://www.researchobject.org/ro-crate/1.1/terminology). 

The `Root(r)` is a type of `Dataset(r)`, and must as metadata have at least the attributes `name`, `description` and `datePublished`, as well as a contextual entity that identify its `license`. These predicates correspond to the RO-Crate 1.1 [minimal requirements for the root data entity](https://www.researchobject.org/ro-crate/1.1/root-data-entity.html#direct-properties-of-the-root-data-entity).

The concept of an `Entity(e)` is introduced as being either a `DataEntity(e)`, a `ContextualEntity(e)`, or [both](https://www.researchobject.org/ro-crate/1.1/contextual-entities.html#contextual-vs-data-entities). Any `Entity(e)` must be typed with at least one `Class(c)`, and every `ContextualEntity(e)` must also have a `name(e,n)`; this corresponding to expectations for any _referenced contextual entity_ (see section on [contextual entities](../#contextualentities)). 

For simplicity in this formalization (and to assist production rules below) `R` is a constant representing a single RO-Crate, typically written to independent RO-Crate Metadata files. `R` is used by `Mentions(R, e)` to indicate that `e` is an Entity described by the RO-Crate and therefore its metadata (a set of Relation and Attribute predicates) form part of the RO-Crate serialization. `Relation(s, p, o)` and `Attribute(s, p, x)` are defined as a _subject-predicate-object_ triple pattern from an `Entity(s)` using a `Property(p)` to either another `Entity(o)` or a `Literal(x)` value.


### Example of formalised RO-Crate 

The below is an example RO-Crate represented using the above formalization, assuming a base IRI of `http://example.com/ro/123/`:

```
RO-Crate(<http://example.com/ro/123/>)
name(<http://example.com/ro/123/, 
    “Data files associated with the manuscript:Effects of …”)
description(<http://example.com/ro/123/, 
    “Palliative care planning for nursing home residents …")
license(<http://example.com/ro/123/>, 
    <https://spdx.org/licenses/CC-BY-4.0>
datePublished(<http://example.com/ro/123/>, “2017")
hasPart(<http://example.com/ro/123/>, <http://example.com/ro/123/survey.csv>)
hasPart(<http://example.com/ro/123/>, <http://example.com/ro/123/interviews/>)

ContextualEntity(<https://spdx.org/licenses/CC-BY-4.0>)
name(<https://spdx.org/licenses/CC-BY-4.0, 
    “Creative Commons Attribution 4.0”)

ContextualEntity(<https://spdx.org/licenses/CC-BY-NC-4.0>)
name(<https://spdx.org/licenses/CC-BY-NC-4.0, 
    “Creative Commons Attribution Non Commercial 4.0”)

File(<http://example.com/ro/123/survey.csv>)
name(<http://example.com/ro/123/survey.csv>, “Survey of care providers”)

Dataset(<http://example.com/ro/123/interviews/>)
name(<http://example.com/ro/123/interviews/>, 
    “Audio recordings of care provider interviews”)
license(<http://example.com/ro/123/interviews/>, 
    <https://spdx.org/licenses/CC-BY-NC-4.0>

```

Notable from this triple-like formalization is that a RO-Crate R is fully represented as a tree at depth 2 helped by the use of `𝕀𝕣𝕚` nodes. For instance the aggregation from the root entity `hasPart(…interviews/>)` is at same level as the data entity’s property `license(…CC-BY-NC-4.0>)` and that contextual entity’s attribute name `(…Non Commercial 4.0”)`. As shown in section [RO-Crate JSON-LD](../#jsonld), the RO-Crate Metadata File serialization is an equivalent shallow tree, although at depth 3 to cater for the JSON-LD preamble of `"@context"` and `"@graph"`.

In reality many additional attributes and contextual types from Schema.org types like <http://schema.org/affiliation> and <http://schema.org/Organization> would be used to further describe the RO-Crate and its entities, but as these are optional (_SHOULD_ requirements) they do not form part of this formalization.


### Mapping to RDF with Schema.org

A formalised RO-Crate can be mapped to different serializations. Assume a simplified[^7] language `𝕃ʀᴅꜰ` based on the RDF abstract syntax [[98]](https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/):

```
                𝕃𝖗𝖉𝖋 = { Triple(s,p,o), IRI(i), BlankNode(b), Literal(s),
                         𝕀𝕣𝕚, ℝ, 𝕊 }
                𝔻𝖗𝖉𝖋 = 𝕊
           ∀i IRI(i) ⇒ i ∈ 𝕀𝕣𝕚
∀s∀p∀o Triple(s,p,o) ⇒（ IRI(s) ∨ BlankNode(s) ）∧
                        IRI(p) ∧
                      （ IRI(o) ∨ BlankNode(o) ∨ Literal(o) ）
          Literal(v) ⊨ Value(v) ∧ Datatype(v,t) ∧ IRI(t)
         ∀v Value(v) ⇒ v ∈ 𝕊
    LanguageTag(v,l) ≡ Datatype(v,
          http://www.w3.org/1999/02/22-rdf-syntax-ns#langString)
```

Below follows a mapping from `𝕃𝖗𝖔𝖈𝖗𝖆𝖙𝖊` to `𝕃𝖗𝖉𝖋` using Schema.org.

```
        Property(p) ⇒ type(p,
             <http://www.w3.org/2000/01/rdf-schema#Property>)
           Class(c) ⇒ type(c,
             <http://www.w3.org/2000/01/rdf-schema#Class>)
         Dataset(d) ⇒ type(d, <http://schema.org/Dataset>)
            File(f) ⇒ type(f, <http://schema.org/MediaObject>)
ContextualEntity(e) ⇒ type(e, <http://schema.org/Thing>)
    CreativeWork(e) ⇒ ContextualEntity(e) ∧
                        type(e, <http://schema.org/CreativeWork>)
      hasPart(e, t) ⇒ Relation(e, <http://schema.org/hasPart>, t)
         name(e, n) ⇒ Attribute(e, <http://schema.org/name>, n)
  description(e, s) ⇒ Attribute(e, <http://schema.org/description>, s)
datePublished(e, d) ⇒ Attribute(e, <http://schema.org/datePublished>, d)
      license(e, l) ⇒ Relation(e, <http://schema.org/license>, l) ∧
                      CreativeWork(l)
         type(e, t) ⇒ Relation(e,
             <http://www.w3.org/1999/02/22-rdf-syntax-ns#type>, t) ∧
                      Class(t)
          String(s) ≡ Value(s) ∧  s ∈ 𝕊
          String(s) ⇒ Datatype(s, 
             <http://www.w3.org/2001/XMLSchema#string>)
         Decimal(d) ≡ Value(d) ∧  d ∈ ℝ
         Decimal(d) ⇒ Datatype(d,
             <http://www.w3.org/2001/XMLSchema#decimal>)
    Relation(s,p,o) ⇒ Triple(s,p,o) ∧ IRI(s) ∧ IRI(o)
   Attribute(s,p,o) ⇒ Triple(s,p,o) ∧ IRI(s) ∧ Literal(o)

```

Note that in the JSON-LD serialization of RO-Crate the expression of `Class` and `Property `is typically indirect: The JSON-LD `@context` maps to Schema.org IRIs, which, when resolved as Linked Data, embeds their formal definition as RDFa. Extensions may however include such term definitions directly in the RO-Crate.


### RO-Crate 1.1 Metadata File Descriptor

An important RO-Crate principle is that of being **self-described**. Therefore the serialization of the RO-Crate into a file should also describe itself in a [Metadata File Descriptor](https://www.researchobject.org/ro-crate/1.1/root-data-entity.html#ro-crate-metadata-file-descriptor), indicating it is `about` (describing) the RO-Crate root data entity, and that it `conformsTo` a particular version of the RO-Crate specification:

```
               about(s,o) ⇒  Relation(s, <http://schema.org/about>, o)
          conformsTo(s,o) ⇒  Relation(s, 
                               <http://purl.org/dc/terms/conformsTo>, R)
MetadataFileDescriptor(m) ⇒ （ CreativeWork(m) ∧ about(m,R) ∧ ROCrate(R) ∧ 
                             conformsTo(m,
                               <https://w3id.org/ro/crate/1.1>) ）
```

Note that although the metadata file necessarily is an _information resource_ written to disk or served over the network (as JSON-LD), it is not considered to be a contained _part_ of the RO-Crate in the form of a _data entity_, rather it is described only as a _contextual entity_.

In the conceptual model the _RO-Crate Metadata File_ can be seen as the top-level node that describes the _RO-Crate Root_, however in the formal model (and the JSON-LD format) the metadata file descriptor is an additional contextual entity that is not affecting the depth-limit of the RO-Crate.


### Forward-chained Production Rules for JSON-LD

Combining the above predicates and Schema.org mapping with rudimentary JSON templates, these forward-chaining production rules can output JSON-LD according to the RO-Crate 1.1 specification[^2]:

```
 Mentions(R, s) ∧ Relation(s, p, o) ⇒  Mentions(R, o)
                             IRI(i) ⇒ "i"
                         Decimal(d) ⇒  d
                          String(s) ⇒ "s"
                     ∀e∀t type(e,t) ⇒  { "@id": s,
                                         "@type": t }
                                       }     
             ∀s∀p∀o Relation(s,p,o) ⇒  { "@id": s,
                                         p: { "@id": o }
                                       }     
            ∀s∀p∀v Attribute(s,p,v) ⇒  { "@id": s,
                                         p: v 
                                       }
                   ∀r∀c  ROCrate(R) ⇒  { "@graph": [ 
                                           Mentions(r, c)* 
                                         ]
                                       }
                                  R ⊨  <./>
                                  R ⇒ MetadataFileDescriptor(
                                        <ro-crate-metadata.json>) 
```

This exposes the first order logic domain of discourse of IRIs, with rational numbers and strings as their corresponding JSON-LD representation. These production rules first grow the graph of `R` by adding a transitive rule that anything described in `R` which is related to `o` means that `o` is also considered mentioned by the RO-Crate `R`. For simplicity this rule is one-way; in theory the JSON-LD graph can also contain free-standing contextual entities that have outgoing relations to data- and contextual entities, but these are proposed to be bound to the root data entity with Schema.org relation <http://schema.org/mentions>.

----

_This is an appendix to the paper [Packaging research artefacts with RO-Crate](../) by Stian Soiland-Reyes, Peter Sefton, Mercè Crosas, Leyla Jael Castro, Frederik Coppens, José M. Fernández, Daniel Garijo, Björn Grüning, Marco La Rosa, Simone Leo, Eoghan Ó Carragáin, Marc Portier, Ana Trisovic, RO-Crate Community, Paul Groth, Carole Goble._

[^2]:
    Limitations: Contextual entities not related from the RO-Crate (e.g. using inverse relations to a data entity) would not be covered by the single direction `Mentions(R, s)` production rule; see [issue 122](https://github.com/ResearchObject/ro-crate/issues/122). The `datePublished(e, d)` rule do not include syntax checks for the ISO 8601 datetime format. Compared with RO-Crate examples, this generated JSON-LD does not use a `@context` as the IRIs are produced unshortened, a post-step could do JSON-LD Flattening with a versioned RO-Crate context. The `@type` expansion is included for clarity, even though this is also implied by the `type(e, t)` expansion to `Relation(e, xsd:type)`.

[^7]: This simplification and mapping does not cover the extensive list of literal datatypes built into RDF 1.1, only strings and decimal real numbers. Likewise, `LanguageTag` is deliberately not utillised below.

[^8]: The full list of types, relations and attribute properties from the RO-Crate specification are not included. Examples shown include `datePublished`, `CreativeWork` and `name`.

[^9]:
    For simplicity, blank nodes are not included in this formalization, as RO-Crate 
    [recommends the use of IRI identifiers](https://www.researchobject.org/ro-crate/1.1/appendix/jsonld.html#describing-entities-in-json-ld)