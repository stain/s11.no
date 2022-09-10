---
title: 'Locating provenance for a RESTful web service'
date: Tue, 02 Apr 2013 16:00:38 +0000
draft: false
tags: ['PROV', 'Tools', 'Tutorials']
---

This blog post shows how RESTful web services can provide, and link to, provenance data for their exposed resources by using the [PROV-AQ](http://www.w3.org/TR/prov-aq/ "PROV-AQ: Provenance access and query") mechanism of HTTP Link headers. This is demonstrated by showing how to update a _hello world_ REST service implemented with Java and [JAX-RS 2.0](http://jax-rs-spec.java.net/nonav/2.0-SNAPSHOT/apidocs/index.html "JAX-RS 2.0-SNAPSHOT javadocs") to provide these links. The  [PROV-AQ HTTP mechanism](http://www.w3.org/TR/prov-aq/#resource-accessed-by-http "Resource accessed by HTTP") is easiest explained by an example: 

```http
GET http://example.com/resource.html HTTP/1.1
Accept: text/html

HTTP/1.1 200 OK
Content-type: text/html
Link: <http://example.com/resource-provenance>; 
         rel="http://www.w3.org/ns/prov#has_provenance"; 
         anchor="http://example.com/resource"

<html>
  <!-- ... -->
</html>
```

This request for `http://example.com/resource.html` returns some HTML, but also provides a `Link:` header that says that the provenance is located at `http://example.com/resource-provenance`. Within this file, the resource is known as the _anchor_ `http://example.com/resource` rather than `http://example.com/resource.html`. The anchor URI can be omitted if it is the same as the one requested. Link headers are specified by [RFC 5988](http://tools.ietf.org/html/rfc5988 "RFC5988 Web linking"), which also defines standard relations like `rel="previous"`. PROV-AQ uses `rel="http://www.w3.org/ns/prov#has_provenance"` to say that the linked resource has the provenance data for the requested resource. PROV-AQ also defines other relations for [provenance query services](http://www.w3.org/TR/2013/WD-prov-aq-20130312/#specifying-provenance-query-services "PROV-AQ: Specifying provenance query services") and [provenance pingback](http://www.w3.org/TR/2013/WD-prov-aq-20130312/#forward-provenance "PROV-AQ: Forward provenance"), which is not covered by this blog post.

Background
==========

[RESTful web services](http://shop.oreilly.com/product/9780596529260.do "Leonard Richardson, Sam Ruby: RESTful Web Services"), or "[Web APIs](http://en.wikipedia.org/wiki/Web_API "Wikipedia: Web API")", are popular ways of exposing structured data on the web, in addition to providing simple ways to programmatically access popular services such as [Twitter](https://dev.twitter.com/docs/api "Twitter REST API"), [Dropbox](https://www.dropbox.com/developers/core/api "Dropbox REST API") and [Google+](https://developers.google.com/+/api/ "Google+ REST API"). Using REST with RDF forms the foundation for [Linked Data](http://linkeddata.org/ "Linked Data"), which has grown to become a standardized way to expose and interrelate public datasets, such as from [data.gov.uk](http://data.gov.uk/linked-data "Linked Data at data.gov.uk").  The web standardization consortium [W3C](http://www.w3.org/) and its [provenance working group](http://www.w3.org/2011/prov/ "W3C Provenance working group") has published the [PROV family of specifications](http://www.w3.org/TR/prov-overview/ "W3C PROV family of provenance specifications") for describing provenance data, in particular a [PROV primer](http://www.w3.org/TR/prov-primer/ "PROV primer") that introduces the PROV data model, and [PROV-O](http://www.w3.org/TR/prov-o/ "PROV-O"), an [OWL](http://www.w3.org/TR/owl2-primer/ "W3C: OWL2 Primer") ontology for using the PROV data model in RDF. In order to suggest a common way to _locate_ such provenance data for a given web resource, the provenance working group has proposed the note [PROV-AQ: Provenance access and query](http://www.w3.org/TR/prov-aq/ "PROV-AQ: Provenance access and query") (PAQ). This note specifies how to locate provenance by a general [HTTP resource](http://www.w3.org/TR/prov-aq/#resource-accessed-by-http "Resource accessed by HTTP"),  from within an [HTML document](http://www.w3.org/TR/prov-aq/#resource-represented-as-html "Resource represented as HTML") or within a [RDF representation](http://www.w3.org/TR/prov-aq/#resource-represented-as-rdf "Resource represented as RDF"). In this blog post we demonstrate the first of these, by using HTTP Link headers.

Provenance from a RESTful service in Java
=========================================

The GitHub project [https://github.com/stain/paq/](https://github.com/stain/paq/) contains a simple _Hello World_ service implemented in Java using  [JAX-RS 2.0](http://jax-rs-spec.java.net/nonav/2.0-SNAPSHOT/apidocs/index.html "JAX-RS 2.0-SNAPSHOT javadocs") backed by the library [CXF](http://cxf.apache.org/docs/jax-rs-basics.html "CXF: JAX-RS basics"). There are two branches in this project:

*   _master_ - REST service that can say hello, and return provenance of greeting
*   _paq_ - REST service that also provides link between greeting and its provenance

Below we'll assume you have checked out the _master_ branch with git: https://gist.github.com/stain/5255523 To compile/run, you will need Java and [Maven](http://maven.apache.org/download.cgi): https://gist.github.com/stain/5255614 The base URI should be http://localhost:8080/paq/ unless you modify the port with `mvn -Djetty.port=9999` Check the HelloWorld REST service is working using your favourite HTTP client (e.g. browser or curl in a new terminal window): https://gist.github.com/stain/5255655 You may replace _Alice_ with any name, as long as it is URI escaped: https://gist.github.com/stain/5255666 The code for this resource is quite straight forward. From [`Helloworld.hello()`](https://github.com/stain/paq/blob/master/src/main/java/com/example/provaq/rest/HelloWorld.java#L22): https://gist.github.com/stain/5255720

Provenance resource
-------------------

This example service provide [provenance](http://www.w3.org/TR/prov-overview/), using the [PROV-N](http://www.w3.org/TR/prov-n/) format: https://gist.github.com/stain/5255675 Note that we used the `-i` parameter above to verify that the correct media-type [text/provenance-notation](http://www.iana.org/assignments/media-types/text/provenance-notation) was returned. This provenance says that the resource [http://localhost:8080/paq/hello/Alice](http://localhost:8080/paq/hello/Alice) was derived from a name with value "Alice", and made by the (web) service [http://localhost:8080/paq/hello](http://localhost:8080/paq/hello). This PROV-N trace is generated by [`HelloWorld.helloProvenance()`](https://github.com/stain/paq/blob/master/src/main/java/com/example/provaq/rest/HelloWorld.java#L30) by filling in the URIs and name in the template [src/main/resources/provTemplate.txt](https://github.com/stain/paq/blob/master/src/main/resources/provTemplate.txt) - a more detailed provenance trace might include things like timestamps and details about who provided the name, and might, through content-negotation, be provided in different representations such as [PROV-O](http://www.w3.org/TR/prov-o/ "W3C: The PROV ontology (PROV-O)") and [PROV-XML](http://www.w3.org/TR/prov-xml/ "W3C: The PROV XML Schema (PROV-XML)"). Our provenance method is a bit more complicated than `hello()` as it [generates the absolute URIs](http://cxf.apache.org/docs/jax-rs-basics.html#JAX-RSBasics-URIcalculationusingUriInfoandUriBuilder) for the greeting resource (depending on the name parameter) and then build the PROV-N trace - here using a simple [MessageFormat](http://docs.oracle.com/javase/7/docs/api/java/text/MessageFormat.html) template: https://gist.github.com/stain/949384558bf8764efddf

Providing links to the provenance
---------------------------------

A restful client who has requested [http://localhost:8080/paq/hello/Alice](http://localhost:8080/paq/hello/Alice) will not magically know that there is a provenance trace at [http://localhost:8080/paq/provenance/hello/Alice](http://localhost:8080/paq/provenance/hello/Alice) - the URI for the provenance resource could just as well have been say [http://localhost:8080/about/history/1337](http://localhost:8080/about/history/1337). As we described above, the PROV-AQ says that a [resource accessed by HTTP](http://www.w3.org/TR/2013/WD-prov-aq-20130312/#resource-accessed-by-http) can describe its provenance trace by adding a `Link:` header with the relation `"http://www.w3.org/ns/prov#has_provenance"`. So in our case, this can be achieved with: https://gist.github.com/stain/5255791 In order to provide the RESTful links we will need to insert `Link:` headers in the `hello()` response. As we need to return both the greeting and HTTP headers, we change our return to a [Response](http://jax-rs-spec.java.net/nonav/2.0-SNAPSHOT/apidocs/javax/ws/rs/core/Response.html "javax.ws.rs.core.Response"): https://gist.github.com/stain/5255833 We'll inject the same `@Context UriInfo ui` parameter as in  `helloProvenance()` in order to find the absolute URIs needed for the provenance link: https://gist.github.com/stain/5255846 and then build a new [Link](http://jax-rs-spec.java.net/nonav/2.0-SNAPSHOT/apidocs/javax/ws/rs/core/Link.html) instance  `provLink`: https://gist.github.com/stain/5255850 This uses the fixed URI for the provenance relation: https://gist.github.com/stain/5255855 Finally we include the new  `Link:` header by adding `provLink` to the response builder before returning: https://gist.github.com/stain/5255859 The [prov-aq-enhanced version of hello()](https://github.com/stain/paq/blob/paq/src/main/java/com/example/provaq/rest/HelloWorld.java#L28) should then look like: https://gist.github.com/stain/5255891 You may check out the [`paq`](https://github.com/stain/paq/tree/paq) branch to see the [prov-aq-enhanced HelloWorld.java](https://github.com/stain/paq/blob/paq/src/main/java/com/example/provaq/rest/HelloWorld.java).

Finding the provenance links
============================

If you have not followed the tutorial above, make sure you **check out** the `paq` branch from [https://github.com/stain/paq](https://github.com/stain/paq) to include the PROV-AQ Link headers. If you are still running the web server from above, stop it with **Ctrl-C**.  Now change to the **paq** branch and restart the server: https://gist.github.com/stain/5255982 Now retrieving the hello world resource with `-i` should show us the new `Link:` header: https://gist.github.com/stain/5256011 Just to verify we did generate our absolute URIs right above, we follow the link: https://gist.github.com/stain/5256018 Let's try to do some hackish shell script to extract this URL: https://gist.github.com/stain/5256036 _Note, the above will not work if the Link header spans multiple lines, which would be legal according to HTTP 1.1 and RFC 5988._ If we now have a [ProvToolbox](https://github.com/lucmoreau/ProvToolbox) installed, we can generate a diagram. The [below shell script paq2svg.sh](https://gist.github.com/stain/5256128/raw/483b96c4317d4416dbd9c6c366ebcf9bc4920c28/paq2svg.sh "paq2svg.sh") assumes that [toolbox-0.1.3-release.zip](http://openprovenance.org/java/maven-releases/org/openprovenance/prov/toolbox/0.1.3/toolbox-0.1.3-release.zip) was unzipped into `$HOME/software/provToolbox`: 


```bash
#!/bin/bash

set -e

PROVTOOLBOX="$HOME/software/provToolbox"
PROVCONVERT="$PROVTOOLBOX/bin/provconvert"

provUri=`curl -s -I $1 | grep ^Link:.*has_provenance  | sed 's/.*<//' | sed 's/>.*//' | head -n 1`

provn=/tmp/$$.provn

curl -s -o $provn $provUri

svg=/tmp/$$.svg

cd $PROVTOOLBOX
$PROVCONVERT -infile $provn -outfile $svg
echo "Created $svg"
```

Running this against the Alice helloworld URI should look up the PROV-AQ header, download the provenance, and then generate an SVG diagram using `provconvert`: 

    stain@ralph-ubuntu:~/src/paq$ ./paq2svg.sh http://localhost:8080/paq/hello/Alice
    InteropFramework run() -> {hello=http://localhost:8080/paq/hello/, app=http://localhost:8080/paq/}
    log4j:WARN No appenders could be found for logger (org.openprovenance.prov.interop.InteropFramework).
    log4j:WARN Please initialize the log4j system properly.
    log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
    ProvToDot role no label
    ProvToDot role no label (by default)
    Created /tmp/21903.svg

An example of this diagram for Alice, converted to PNG: 

![PROV diagram, Alice pointing to name (derivation) and hello (attribution)](alice.png)