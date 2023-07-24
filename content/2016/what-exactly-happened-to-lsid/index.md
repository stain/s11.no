---
title: "What exactly happened to LSID?"
date: 2016-02-26
lastmod: 2023-07-24
tags:
  - academic
  - Linked Data
keywords:
  - identifier
  - life sciences
  - LSID
  - URI
categories:
  - Archive
citeas: https://doi.org/10.5281/zenodo.46804
authors:
  - name: Stian Soiland-Reyes
    orcid: https://orcid.org/0000-0001-9842-9718
  - name: Alan R Williams
    orcid: https://orcid.org/0000-0003-3156-2105
summary: |
  What exactly happened to LSID? It was a technically sound approach it
  would seem and one whose failure we would do well to learn more from.
---


> What exactly happened to LSID? It was a technically sound approach it
> would seem and one whose failure we would do well to learn more from.

## Cite as

Stian Soiland-Reyes, Alan R Williams (2016):\
**What exactly happened to LSID?**\
*myGrid developer blog*, 2016-02-26.\
<https://doi.org/10.5281/zenodo.46804>


------------------------------------------------------------------------

# What exactly happened to LSID?

-   Stian Soiland-Reyes, [eScience Lab, University of Manchester](http://www.esciencelab.org.uk/)\
    <https://orcid.org/0000-0001-9842-9718>
-   Alan R Williams, [eScience Lab, University of Manchester](http://www.esciencelab.org.uk/)\
    <https://orcid.org/0000-0003-3156-2105>


**Life Science Identifiers**
([LSID](https://en.wikipedia.org/wiki/LSID))
was an identification scheme for identifying Life Science information,
e.g. describing genes, proteins, species. It was created by the
bioinformatics community, and standardized in 2004 as an [LSID
specification](http://www.omg.org/cgi-bin/doc?dtc/04-05-01) [[archived 2023-07-24](https://web.archive.org/web/20230724155313/https://www.omg.org/cgi-bin/doc?dtc/04-05-01.pdf)]
through the [Object Management Group](http://www.omg.org/).
As of 2016 it is no longer used, except within the biodiversity
community for [identifying species](http://www.ipni.org/) [[archived 2017-07-12](https://web.archive.org/web/20170712042244/http://www.ipni.org/lsids.html)].

LSID overview
-------------

The [[LSID specification](http://www.omg.org/cgi-bin/doc?dtc/04-05-01)
specifies 4 aspects of LSIDs:

-   *LSID Syntax* specifying a [URN scheme](https://en.wikipedia.org/wiki/Uniform_Resource_Name),
    e.g. `URN:LSID:rcsb.org:PDB:1D4X:22`
-   *LSID Resolution Service*, an API for retrieving data and metadata
    for a given LSID
-   *LSID Resolution Discovery Service* -- an API for finding LSID
    Resolution Services for a given LSID namespace
-   *LSID Assigning Service* -- an API for minting new LSIDs

The APIs were specified as Java interfaces,  [WSDL Web
Services](https://en.wikipedia.org/wiki/Web_Services_Description_Language)
(SOAP and basic WSDL bindings for HTTP `GET` and FTP retrieval). The
specification suggests a method for registering LSID Resolution Services
through [`SRV` records](https://en.wikipedia.org/wiki/SRV_record) in DNS.

The aims of LSIDs in 2004 were certainly promising:

> LSIDs are expressed as a URN namespace and share the following
> functional capabilities of URNs:
>
> -   **Global scope**: A LSID is a name with global scope that does not
>     imply a location. It has the same meaning everywhere.
> -   **Global uniqueness**: The same LSID will never be assigned to two
>     different objects
> -   **Persistence**: It is intended that the lifetime of an LSID be
>     permanent. That is, the LSID will be globally unique forever, and
>     may be used as a reference to an object well beyond the lifetime
>     of the object it identifies or of any naming authority involved in
>     the assignment of its name.
> -   **Scalability**: LSIDs can be assigned to any data element that
>     might conceivably be available on the network, for hundreds of
>     years
> -   **Legacy Support**: The LSID naming scheme must permit the support
>     of existing legacy naming systems, insofar as they meet the
>     requirements specified below.
> -   **Extensibility**: Any scheme for LSIDs must permit future
>     extensions to the scheme.
> -   **Independence**: It is solely the responsibility of a name
>     issuing authority to determine conditions under which it will
>     issue a name.
> -   **Resolution**: A URN will not impede resolution (translation to a
>     URL).
>
> <small>Source: [Life Sciences Identifiers Specification, page
> 15](http://www.omg.org/cgi-bin/doc?dtc/04-05-01.pdf#page=15)</small>

So what went wrong?
-------------------

The short answer is that LSID did not receive enough uptake. But we
think the real reason for that is more complicated.

Lack of support from main actors
--------------------------------

Lack of uptake might partially be because the importance of global
identifiers in Life Sciences, although well known at the time (and 
obviously causing LSID to be created), did not receive enough focus from
upstream bodies like funders, institutions and even PIs, and remained a
niche for the Semantic Web branch of Life Science data management.

Many large data providers in life sciences did not adapt LSIDs, probably
because it meant too many changes to their architecture. Thus the
exposure, knowledge and skills around LSIDs did not propagate to the
masses.

Data Management Policies (which would require repositories with
identifiers for deposits) were in their infancy at the time, now they
are pretty much mandated both by
[funders](https://www.ukri.org/manage-your-award/publishing-your-research-findings/making-your-research-data-open/) [[archived 2016-12-18](https://web.archive.org/web/20161218065042/http://www.rcuk.ac.uk/research/datapolicy/)]
and
[institutions](https://www.library.manchester.ac.uk/services/research/research-data-management/policies/) [archived 2016-07-26](https://web.archive.org/web/20160726164036/http://www.library.manchester.ac.uk/services-and-support/staff/research/services/research-data-management/policy/).

Technically there are of course many other potential reasons why LSID
failed, which would have influenced the social-political attitudes.

### New URI scheme

LSIDs use a its own URN scheme `urn:lsid`, which was not supported by
browsers or operating systems.

Adding support for resolving a sub-scheme of `urn`:  to browsers seemed
difficult as it meant handling the whole `urn`:   scheme, some even used
another URI scheme [`lsidres:` as a
workaround](https://sourceforge.net/p/lsid/mailman/message/1002397/).

If LSIDs were linked to at all, then most common would be
application-specific `http://` links which embeds the LSID somewhere in
its path or parameters, e.g.
~~<http://ipni.org/urn:lsid:ipni.org:names:986604-1:1.1.2.1.1.2>`` [[now <http://ipni.org/urn:lsid:ipni.org:names:986604-1>]]
which uses HTTP [303 See Other](https://en.wikipedia.org/wiki/HTTP_303)
redirects to a HTML representation on ~~<http://www.ipni.org/ipni/plantNameByVersion.do?id=986604-1&version=1.1.2.1.1.2&output\_format=lsid-metadata&show\_history=true>~~
[[now <https://ipni.org/n/986604-1>]] [[alternative archived 2011-06-22](https://web.archive.org/web/20110622063128/http://ipni.org/ipni/plantNameByVersion.do;jsessionid=002B3F489727A748FE733A1D420213CB?id=46732-1&version=1.1.2.2.1.1&output_format=lsid-metadata&show_history=true)] 
(and thus is a [Cool
URI](https://www.w3.org/TR/cooluris/#r303uri))

`urn:lsid` was never [registered with
IANA](http://www.iana.org/assignments/urn-namespaces/)
as an official  namespace and so remained an non-standard scheme.

Dependency on DNS records
-------------------------

While an LSID promised to be *location independent* (allowing multiple
sources to describe the same object)*,* and had provisioning for
multiple alternative LSID resolvers to be discovered via
~~<https://web.archive.org/web/20200805021230/http://lsidauthority.org/>~~
[[archived 2012 as a broken redirect](https://web.archive.org/web/20120117034941/http://lsidauthority.org/)]
-- this never manifested, and in practice LSID was bound to a DNS domain
name.

For such an LSID to be resolvable without additional configuration, 
this required technical changes to the DNS records. At the time, most
Life Science web services were not even using DNS CNAMEs to provide
service names (e.g. `repository.example.com`), and Web Service URLs like
`http://underthedesk18762.institute.example.edu:8081/~phdstudent5/service2.cgi`
were unfortunately very common.

Asking such service providers to modify (and maintain!) their DNS SRV
records was probably asking for too much. (As a side-note, the required
SRV service type was [not registered with IANA](http://www.iana.org/assignments/service-names-port-numbers/)
either).

In practice the reference implementation LSID Resolver Service also
needed to run on its own port, which required it to work through
firewall changes.

The end result was that most LSIDs you could find during the 2000s were
not resolvable through the LSID Resolution mechanism unless you knew by
hard-coding where the LSID Resolution Service was hosted.

Difficult to resolve
--------------------

While tools like
[BioJava](https://biojava.org/) [[archived 2016-05-07](https://web.archive.org/web/20160507003719/http://biojava.org/)]
included support for resolving LSIDs (downloading the data), practically
LSIDs were not used for resolution programmatically, at least not
through the LSID Resolution Service.

This could be because these services were difficult to find (see DNS
section above), or poorly maintained (running on a separate port, often
down for weeks until someone notice), or difficult to call (required
SOAP libraries, which in the early 2000s suffered from many
incompatibility issues).

In practice LSIDs were resolved as in the ipni.org example, with simple
HTTP redirects from simple HTTP URIs, but from services which only
supported "their own" LSIDs. Such HTTP redirections are simple to
support in pretty much any server frameworks and client libraries.

And so this begs the  question -- what makes an LSID different from a
plain old HTTP URI?

So the LSID design suffered with a requirements for resolution that made
it trickier (or at least gave the impression of being trickier) to use
and mint, but in the end only the identifier bit of LSID was used.

Lack of metadata requirements
-----------------------------

LSID had provisioning to ask for metadata in addition to the data,
having two methods `getData()` and `getMetadata()`

While keeping a clear distinction between data and metadata seems like a
good idea, in practice it can be quite hard as one researcher's metadata
is another researchers data.  There's also the question if this is the
metadata about the *identifier*, (e.g. allocated in April 2004),   the
metadata about the *record* (e.g. last updated in 2014), or the metadata
about the *thing* (e.g. discovered in 1823).

Often the distinction between a thing and the description about the
thing can be blurry, which is a well known problem for the Semantic Web
([httpRange-14](https://en.wikipedia.org/wiki/HTTPRange-14)).
Additionally many data formats include their own metadata mechanism,
e.g. [FASTA headers](https://www.uniprot.org/help/fasta-headers) 
[[archived 2017-07-02](https://web.archive.org/web/20170702124543/http://www.uniprot.org/help/fasta-headers)],
which could be hard to keep in sync with the metadata in the LSID
record.

The reference implementation for the LSID Allocation Service did not
require any particular metadata, which meant that in practice you could
get away with no metadata at all.

LSID metadata was provided in RDF, which at the time had poor
application library support, forcing many to hand-write metadata in the
awkward
[RDF/XML](https://www.w3.org/TR/rdf-syntax-grammar/)
format (since replaced by
[JSON-LD](https://www.w3.org/TR/json-ld/)
and
[Turtle](https://www.w3.org/TR/turtle/)).

The landscape of RDF vocabularies and ontologies for describing
biological information was quite rough in the 2000s, with many
incompatible or confusing approaches, often require a full "*buy in*" to
a particular model. Practically the only commonly used vocabularies at
the time were [Dublin Corev Terms](http://dublincore.org/documents/dcmi-terms/)
and
[FOAF](http://xmlns.com/foaf/spec/)
-- but the LSID specification did not provide any minimal metadata
requirements or guidance on how to form the metadata.

Today the simplicity of DC Terms has evolved to [schema.org](http://schema.org/), useful for all kinds of lightweight metadata,  detailed provenance can
be described with [PROV](https://www.w3.org/TR/prov-o/),
and collective efforts like the [OBO Foundry](https://www.obofoundry.org/)
create domain-specific ontologies.

Rather than distinguishing between data and metadata, today we do
[content-negotiation](https://en.wikipedia.org/wiki/Content_negotiation)
between different formats/representations (e.g. HTML, JSON, XML,
JSON-LD, RDF Turtle), or embed metadata in-line of HTML using
[microformats](http://microformats.org/)
like
[RDFa](https://www.w3.org/TR/rdfa-primer/).

Non-distributed allocation
--------------------------

Allocating LSIDs centrally through an *LSID Allocation Service* was
tricky for distributed architectures, which were popular at the time.

For instance, [Taverna
Workbench](http://www.taverna.org.uk/download/workbench/) [[archived 2020-09-25](https://web.archive.org/web/20200925135310/http://www.taverna.org.uk/download/workbench/)]
version 1, running on desktop computers, used LSIDs to identify every
data item that was created during a workflow run. In theory LSIDs were a
good fit -- as such data don't have a "proper home" yet -- it's still
good to give them identifiers early on and carry it along in the
provenance trace.

But in practice Taverna had to "call home" to mygrid.org.uk's LSID
Allocation Service to get new identifiers. This meant that this LSID
service became a [single point of failure](https://en.wikipedia.org/wiki/Single_point_of_failure)
for any Taverna installation (unless overriden in local configuration),
and any downtime would stop every workflow running. Yet these LSIDs were
allocated blindly and sequentially, we *(deliberately for privacy reasons)*
did not record any metadata beyond "*producer=Taverna*" and
had no ability to resolve the data from the LSID server.

And so in a next version of Taverna we changed the identifier  code to 
generate random
[UUIDs](https://en.wikipedia.org/wiki/Universally_unique_identifier)
locally, and allocated LSIDs like:

    urn:lsid:net.sf.taverna:DataThing:b1b5c94f-d54d-4039-901c-3ad022e5845f

Now what makes that LSID URI any different from an URI with the prefix
[urn:uuid:](https://www.ietf.org/rfc/rfc4122)
or
~~<http://ns.taverna.org.uk/>~~ [[archived 2017-06-03](https://web.archive.org/web/20170503105536/https://taverna.incubator.apache.org/ns/)]
?

HTTP took over -- death of WSDL
-------------------------------

LSIDs are born in the early
[WSDL](https://en.wikipedia.org/wiki/Web_Services_Description_Language)
days. WSDL and SOAP was a glorified
[XML-RPC](https://en.wikipedia.org/wiki/XML-RPC)
message-passing protocol that just happened to run over HTTP -- in
theory you could even transport SOAP messages over email!

WSDL users did not easily agree on common XML schemas, and so each web
service would have its own schema for its operations and results.

So an `<id>` XML field (or was that attribute?) that could be sent
across multiple WSDL services seemed useful -- hence there was a need
for LSID.

There was no need for the LSID to be directly downloadable -- as WSDL
services always ran through a single HTTP endpoint and just modified
which XML message requests were `POST`ed.

But this meant some size challenges, the LSID Resolution protocol is
primarily WSDL based, which proved tricky with the `getData()` method
returning base64-encoded bytes, which would make the SOAP libraries eat
memory -- anything over 50 MB became "big data"!

In plain HTTP we have known for a long time now to [transfer largish
files](https://tools.ietf.org/html/rfc2068#section-14.36.1),
while LSID had to resolve to a separate byte-range-variant of
`getData()` which, if at all supported, complicated download for
clients.

In 2000, [Roy
Fielding](https://en.wikipedia.org/wiki/Roy_Fielding)
published his PhD thesis [Architectural Styles and the Design of
Network-based Software
Architectures](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)
-- summarised by its mantra "*hypermedia as the engine of application
state*", and effectively establishing the [Representational State
Transfer
(REST)](https://en.wikipedia.org/wiki/Representational_state_transfer)
as the software architectural style of the Web.

REST services are now ubiquitous on the web,  and with
[JSON](http://www.json.org/)
taking over as a much simpler data format than XML, REST now power not
just most [bioinformatics web
services](https://esciencelab.org.uk/products/biocatalogue/) [[archived 2020-08-06](https://web.archive.org/web/20200806012139/https://www.biocatalogue.org/)]
but also today's modern mobile apps and [web applications](https://en.wikipedia.org/wiki/Web_application),
like Facebook, Twitter and GMail.

So with REST the HTTP Resources and their URIs become first citizens
again (rather than WSDLs lonely endpoints). HTTP URIs are resolvable
directly to both human (HTML) and computational representations (JSON,
XML, RDF) thanks to
[content-negotiation](https://en.wikipedia.org/wiki/Content_negotiation).

So I can use <http://purl.uniprot.org/uniprot/P99999> [[archived 2017-09-25](https://web.archive.org/web/20170925085508/http://purl.uniprot.org/uniprot/P99999)]
to refer to a protein, and even if you have no special code to resolve
this, you can just paste the link into your browser and read about
*Cytochrome c* protein. But if you [retrieve that Uniprot URI as Linked
Data](http://rdf.greggkellogg.net/distiller?in_fmt=rdfxml&minimal=true&uri=http:%2F%2Fpurl.uniprot.org%2Funiprot%2FP99999&command=serialize&format=rdfxml&output_format=turtle&url=http:%2F%2Fpurl.uniprot.org%2Funiprot%2FP99999) [[not archived]],
then you can [programmatically
access](https://www.uniprot.org/help/programmatic_access) [[archived 2017-08-06](https://web.archive.org/web/20170806092501/http://www.uniprot.org/help/programmatic_access)]
the data, or retrieve just the [FASTA
sequence](https://www.uniprot.org/uniprot/P12345.fasta) [[archived 2019-08-28](https://web.archive.org/web/20190828213820/https://www.uniprot.org/uniprot/P12345.fasta]). 
Even as a uniprot.org assigned identifier, the URI works well with
third-party APIs, e.g. with with [Open
PHACTS](https://esciencelab.org.uk/projects/openphacts/) [[archived 2017-08-14](https://web.archive.org/web/20170814105641/http://www.openphacts.org/)]
to retrieve the [related
pathways](https://web.archive.org/web/20200805021230/https://beta.openphacts.org/2.0/pathways/byTarget?uri=http%3A%2F%2Fpurl.uniprot.org%2Funiprot%2FP99999&app_id=161aeb7d&app_key=333c09ae195d777b68a117bb42f29b1c).

As a plain old URI, <http://purl.uniprot.org/uniprot/P99999>
can be added to web pages, publications and other repositories without
any further explanation.

Centralization
--------------

Since last decade we have moved back towards centralised architectures.
While our architectures consists of distributed REST services (e.g.
[ElasticSearch](https://www.elastic.co/elasticsearch/) [[archived 2017-08-05](https://web.archive.org/web/20170805070835/https://www.elastic.co/products/elasticsearch)]
and [Apache
CouchDB](https://couchdb.apache.org/) [[archived 2017-08-06](https://web.archive.org/web/20170806095247/http://couchdb.apache.org/)])
and *vertically scalable* platforms (e.g. [Apache
Hadoop](https://hadoop.apache.org/) [[archived 2017-08-04](https://web.archive.org/web/20170804160424/http://hadoop.apache.org/)],
[Docker](https://www.docker.com/) [[archived 2017-08-05](https://web.archive.org/web/20170805050552/https://www.docker.com/)]
microservices), but now it is running on centralised *cloud* *services*
owned by a handful of companies like [Amazon
AWS](https://aws.amazon.com/) [[archived 2017-08-05](https://web.archive.org/web/20170805023840/https://aws.amazon.com/)],
[DigitalOcean](https://www.digitalocean.com/) [[archived 2017-08-04](https://web.archive.org/web/20170804024304/https://www.digitalocean.com/)]
and [Microsoft
Azure](https://azure.microsoft.com/) [[archived 2017-08-04](https://web.archive.org/web/20170804201738/https://azure.microsoft.com/en-us/).

Large data integration efforts like
[Uniprot](https://www.uniprot.org/) [[archived 2017-08-04](https://web.archive.org/web/20170804181944/http://www.uniprot.org/)]
and
[ChEMBL](https://www.ebi.ac.uk/chembl/) [[archived 2017-07-10](https://web.archive.org/web/20170710162120/https://www.ebi.ac.uk/chembl/)]
have also effectively centralised ID allocations in bioinformatics. Yet
after the advent of [next-gen
sequencing](https://www.illumina.com/science/technology/next-generation-sequencing.html) [[archived 2017-07-12](https://web.archive.org/web/20170712122515/https://www.illumina.com/science/technology/next-generation-sequencing.html)]
and [robotic synthesis and
analysis](https://synbiochem.co.uk/facilities/) [[archived 2016-10-29](https://web.archive.org/web/20161029101943/http://synbiochem.co.uk/facilities/)]
we are also producing more data than ever before.

Difficult to integrate
----------------------

This is just speculation, but given the state of Web Services support in
server frameworks at the time of LSID it would be very hard for actors
like EBI and Uniprot to modify their existing web-based services to
support the LSID protocol.

Thus they would need to set up a separate LSID Resolution Service, but
that didn't know anything about their existing ID schemes which
understandably they didn't want to change over night.

Done again today (20/20 hindsight) as a plain HTTP redirection based
service, LSID could easily be implemented even in modern frameworks like
node.js or Ruby on Rails without needing any special libraries.

Conclusion
----------

LSIDs were doing all the "right things" according to its time: defining
a location-independent URN scheme,  using DNS SRV entries, providing
WSDL services, separating data and metadata, using RDF, providing
discovery mechanisms and alternative resolution services.

Yet it can be argued that LSIDs, in many ways just like SOAP, was a
complicated way to replicate something that could already do the job --
the Web and plain-old http:// URIs.

Perhaps we needed to go the long way around to figure it all out.

