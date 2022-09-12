---
title: 'Locating provenance for a RESTful web service'
date: Tue, 02 Apr 2013 16:00:38 +0000
categories:
    - Practical Provenance
tags: ['PROV', 'Tools', 'Tutorials', 'ProvToolbox', 'signposting']
---

This blog post shows how RESTful web services can provide, and link to, provenance data for their exposed resources by using the [PROV-AQ](http://www.w3.org/TR/prov-aq/ "PROV-AQ: Provenance access and query") mechanism of HTTP Link headers. This is demonstrated by showing how to update a _hello world_ REST service implemented with Java and [JAX-RS 2.0](http://jax-rs-spec.java.net/nonav/2.0-SNAPSHOT/apidocs/index.html "JAX-RS 2.0-SNAPSHOT javadocs") to provide these links. 

The  [PROV-AQ HTTP mechanism](http://www.w3.org/TR/prov-aq/#resource-accessed-by-http "Resource accessed by HTTP") is easiest explained by an example: 

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

Below we'll assume you have checked out the _master_ branch with git: 

```
stain@ralph-ubuntu:~/src$ git clone https://github.com/stain/paq.git
Cloning into 'paq'...
remote: Counting objects: 127, done.
remote: Compressing objects: 100% (55/55), done.
remote: Total 127 (delta 26), reused 125 (delta 24)
Receiving objects: 100% (127/127), 35.72 KiB, done.
Resolving deltas: 100% (26/26), done.
```

To compile/run, you will need Java and [Maven](https://maven.apache.org/download.cgi): 

```
stain@ralph-ubuntu:~/src/paq$ mvn clean jetty:run
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Building Example PROV-AQ usage 0.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
(..)
INFO: Root WebApplicationContext: initialization completed in 2462 ms
2013-03-27 16:22:04.566:INFO::Started SelectChannelConnector@0.0.0.0:8080
[INFO] Started Jetty Server
[INFO] Starting scanner at interval of 10 seconds.
```

The base URI should be http://localhost:8080/paq/ unless you modify the port with `mvn -Djetty.port=9999` 

Check the HelloWorld REST service is working using your favourite HTTP client (e.g. browser or curl in a new terminal window): 


```
stain@ralph-ubuntu:~/src/paq$ curl http://localhost:8080/paq/hello/Alice
Hello, Alice
```

You may replace _Alice_ with any name, as long as it is URI escaped: 

```
stain@ralph-ubuntu:~/src/paq$ curl http://localhost:8080/paq/hello/Joe%20Bloggs
Hello, Joe Bloggs
```

The code for this resource is quite straight forward. From [`Helloworld.hello()`](https://github.com/stain/paq/blob/master/src/main/java/com/example/provaq/rest/HelloWorld.java#L22): 


```java
@GET
@Path("hello/{name}")
@Produces("text/plain")
public String hello(@PathParam("name") String name) {
    String greeting = "Hello, " + name + "\n";
    return greeting;
}
```

Provenance resource
-------------------

This example service provide [provenance](http://www.w3.org/TR/prov-overview/), using the [PROV-N](http://www.w3.org/TR/prov-n/) format: 


```shell
stain@ralph-ubuntu:~/src/paq$ curl -i http://localhost:8080/paq/provenance/hello/Alice
HTTP/1.1 200 OK
Content-Type: text/provenance-notation
Date: Wed, 27 Mar 2013 16:27:14 GMT
Content-Length: 305
Server: Jetty(6.1.26)

document
  prefix hello <http://localhost:8080/paq/hello/>
  prefix app <http://localhost:8080/paq/>
  entity(hello:Alice)
  wasDerivedFrom(hello:Alice, name)
  entity(name, [ prov:value="Alice" ])
  agent(app:hello, [ prov:type=prov:SoftwareAgent ])
  wasAttributedTo(hello:Alice, app:hello)
endDocument
```

Note that we used the `-i` parameter above to verify that the correct media-type [text/provenance-notation](http://www.iana.org/assignments/media-types/text/provenance-notation) was returned. 

This provenance says that the resource [http://localhost:8080/paq/hello/Alice](http://localhost:8080/paq/hello/Alice) was derived from a name with value "Alice", and made by the (web) service [http://localhost:8080/paq/hello](http://localhost:8080/paq/hello). 

This PROV-N trace is generated by [`HelloWorld.helloProvenance()`](https://github.com/stain/paq/blob/master/src/main/java/com/example/provaq/rest/HelloWorld.java#L30) by filling in the URIs and name in the template [src/main/resources/provTemplate.txt](https://github.com/stain/paq/blob/master/src/main/resources/provTemplate.txt) - a more detailed provenance trace might include things like timestamps and details about who provided the name, and might, through content-negotation, be provided in different representations such as [PROV-O](http://www.w3.org/TR/prov-o/ "W3C: The PROV ontology (PROV-O)") and [PROV-XML](http://www.w3.org/TR/prov-xml/ "W3C: The PROV XML Schema (PROV-XML)"). 

Our provenance method is a bit more complicated than `hello()` as it [generates the absolute URIs](http://cxf.apache.org/docs/jax-rs-basics.html#JAX-RSBasics-URIcalculationusingUriInfoandUriBuilder) for the greeting resource (depending on the name parameter) and then build the PROV-N trace - here using a simple [MessageFormat](http://docs.oracle.com/javase/7/docs/api/java/text/MessageFormat.html) template: 

```java
    @GET
    @Path("provenance/hello/{name}")
    @Produces("text/provenance-notation")
    public String helloProvenance(@PathParam("name") String name,
            @Context UriInfo ui) throws IOException {
        // Get our absolute URI
        // See http://cxf.apache.org/docs/jax-rs-basics.html#JAX-RSBasics-URIcalculationusingUriInfoandUriBuilder        
        UriBuilder appUri = ui.getBaseUriBuilder();
        // Absolute URIs for resources we are to give provenance about
        URI helloURI = appUri.path(getClass(), "hello").build(name);        
        
        // Prepare prefixes for PROV-N qualified names
        URI appURI = appUri.build("").resolve("../");        
        URI helloPrefix = helloURI.resolve("./");
        
        // The PROV-N qualified name for our /hello/{name} resource
        String helloEntity = "hello:" + helloPrefix.relativize(helloURI);
        
        // Simple PROV-N trace, see <http://www.w3.org/TR/prov-n/>
        // Here this is done in a naive way by loading a template 
        // from src/main/resources and do string-replace to insert
        // our URIs.
        String template = IOUtils.toString(getClass().getResourceAsStream("/provTemplate.txt"));
        String prov = MessageFormat.format(template, 
                helloPrefix, appURI, helloEntity, name);
        // Note: PROV-N should be be built using say the PROV Toolbox 
        // rather than this naive template approach!
        return prov;
    }
}
```


Providing links to the provenance
---------------------------------

A restful client who has requested [http://localhost:8080/paq/hello/Alice](http://localhost:8080/paq/hello/Alice) will not magically know that there is a provenance trace at [http://localhost:8080/paq/provenance/hello/Alice](http://localhost:8080/paq/provenance/hello/Alice) - the URI for the provenance resource could just as well have been say [http://localhost:8080/about/history/1337](http://localhost:8080/about/history/1337). As we described above, the PROV-AQ says that a [resource accessed by HTTP](http://www.w3.org/TR/2013/WD-prov-aq-20130312/#resource-accessed-by-http) can describe its provenance trace by adding a `Link:` header with the relation `"http://www.w3.org/ns/prov#has_provenance"`. So in our case, this can be achieved with: 

```http
Link: <http://localhost:8080/paq/provenance/hello/Alice>;
       rel="http://www.w3.org/ns/prov#has_provenance"
```

In order to provide the RESTful links we will need to insert `Link:` headers in the `hello()` response. As we need to return both the greeting and HTTP headers, we change our return to a [Response](http://jax-rs-spec.java.net/nonav/2.0-SNAPSHOT/apidocs/javax/ws/rs/core/Response.html "javax.ws.rs.core.Response"): 

```java
@GET
@Path("hello/{name}")
@Produces("text/plain")
public Response hello(@PathParam("name") String name) {
    String greeting = "Hello, " + name + "\n";
    ResponseBuilder responseBuilder = Response.ok().entity(greeting);
    return responseBuilder.build();
}
``` 

We'll inject the same `@Context UriInfo ui` parameter as in  `helloProvenance()` in order to find the absolute URIs needed for the provenance link: https://gist.github.com/stain/5255846 and then build a new [Link](http://jax-rs-spec.java.net/nonav/2.0-SNAPSHOT/apidocs/javax/ws/rs/core/Link.html) instance  `provLink`: 

```java
Link provLink = Link.fromUri(provUri).rel(HAS_PROVENANCE).build();
```

This uses the fixed URI for the provenance relation: 

```java
private static final String HAS_PROVENANCE = 
  "http://www.w3.org/ns/prov#has_provenance";
```

Finally we include the new  `Link:` header by adding `provLink` to the response builder before returning: 

```java
return responseBuilder.header(HttpHeaders.LINK, provLink).build();
```

The [prov-aq-enhanced version of hello()](https://github.com/stain/paq/blob/paq/src/main/java/com/example/provaq/rest/HelloWorld.java#L28) should then look like: 

```java
private static final String HAS_PROVENANCE = "http://www.w3.org/ns/prov#has_provenance";

@GET
@Path("hello/{name}")
@Produces("text/plain")
public Response hello(@PathParam("name") String name, @Context UriInfo ui) {
    // TODO: Could have used Link.fromResourceMethod instead, 
    // but it seems to return wrong URI in current CXF
    URI provUri = ui.getBaseUriBuilder().path(getClass(), "helloProvenance").build(name);
    Link provLink = Link.fromUri(provUri).rel(HAS_PROVENANCE).build();

    String greeting = "Hello, " + name + "\n";
    ResponseBuilder responseBuilder = Response.ok().entity(greeting);
    return responseBuilder.header(HttpHeaders.LINK, provLink).build();
}
```

You may check out the [`paq`](https://github.com/stain/paq/tree/paq) branch to see the [prov-aq-enhanced HelloWorld.java](https://github.com/stain/paq/blob/paq/src/main/java/com/example/provaq/rest/HelloWorld.java).


Finding the provenance links
============================

If you have not followed the tutorial above, make sure you **check out** the `paq` branch from [https://github.com/stain/paq](https://github.com/stain/paq) to include the PROV-AQ Link headers. If you are still running the web server from above, stop it with **Ctrl-C**.  Now change to the **paq** branch and restart the server: 

```
stain@ralph-ubuntu:~/src/paq$ git checkout paq
Switched to branch 'paq'

stain@ralph-ubuntu:~/src/paq$ mvn clean jetty:run
[INFO] Scanning for projects...
[INFO]                                                                         
[INFO] ------------------------------------------------------------------------
[INFO] Building Example PROV-AQ usage 0.1-SNAPSHOT
(..)
2013-03-27 16:56:29.565:INFO::Started SelectChannelConnector@0.0.0.0:8080
[INFO] Started Jetty Server
[INFO] Starting scanner at interval of 10 seconds.
```

Now retrieving the hello world resource with `-i` should show us the new `Link:` header: 

```http
stain@ralph-ubuntu:~/src/paq$ curl -i http://localhost:8080/paq/hello/Alice
HTTP/1.1 200 OK
Content-Type: text/plain
Date: Wed, 27 Mar 2013 16:59:46 GMT
Link: <http://localhost:8080/paq/provenance/hello/Alice>;rel=http://www.w3.org/ns/prov#has_provenance
Content-Length: 13
Server: Jetty(6.1.26)

Hello, Alice
```

Just to verify we did generate our absolute URIs right above, we follow the link: 

```sh
stain@ralph-ubuntu:~/src/paq$ curl http://localhost:8080/paq/provenance/hello/Alice
document
  prefix hello <http://localhost:8080/paq/hello/>
  prefix app <http://localhost:8080/paq/>
  entity(hello:Alice)
  wasDerivedFrom(hello:Alice, name)
  entity(name, [ prov:value="Alice" ])
  agent(app:hello, [ prov:type=prov:SoftwareAgent ])
  wasAttributedTo(hello:Alice, app:hello)
endDocument
```

Let's try to do some hackish shell script to extract this URL: 

```sh
stain@ralph-ubuntu:~/src/paq$ curl -s -I http://localhost:8080/paq/hello/Alice | 
   grep ^Link:.*has_provenance  | sed 's/.*<//' | sed 's/>.*//'
http://localhost:8080/paq/provenance/hello/Alice
```

_Note, the above will not work if the Link header spans multiple lines, which would be legal according to HTTP 1.1 and RFC 5988._ 

If we now have a [ProvToolbox](https://github.com/lucmoreau/ProvToolbox) installed, we can generate a diagram. 

The [below shell script paq2svg.sh](https://gist.github.com/stain/5256128/raw/483b96c4317d4416dbd9c6c366ebcf9bc4920c28/paq2svg.sh "paq2svg.sh") assumes that [toolbox-0.1.3-release.zip](http://openprovenance.org/java/maven-releases/org/openprovenance/prov/toolbox/0.1.3/toolbox-0.1.3-release.zip) was unzipped into `$HOME/software/provToolbox`: 

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

```sh
stain@ralph-ubuntu:~/src/paq$ ./paq2svg.sh http://localhost:8080/paq/hello/Alice
InteropFramework run() -> {hello=http://localhost:8080/paq/hello/, app=http://localhost:8080/paq/}
log4j:WARN No appenders could be found for logger (org.openprovenance.prov.interop.InteropFramework).
log4j:WARN Please initialize the log4j system properly.
log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
ProvToDot role no label
ProvToDot role no label (by default)
Created /tmp/21903.svg
```

An example of this diagram for Alice, converted to PNG: ![PROV diagram: Alice derived from name, attributed to hello](alice.png)
