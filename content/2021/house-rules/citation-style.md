---
title: s11 Citation & Bibliography Style Guide
tags:
  - academic
  - citation
---

In academic writing, the s11 House Rules recommend the following bibliography style:

First Author, Second Author, All Authors (year):  
[**Title**](https://doi.org10.1000/123456).  
Event, _Venue_ **issue**  
<https://doi.org/10.1000/123456>

Rationale:
1. It should be possible to write the reference without a bibliography manager
2. All authors SHOULD be credited. We have enough bytes left on the Internet, and _et al._ have high enough h-index already.
3. [Names around the world](https://www.w3.org/International/questions/qa-personal-names) vary in how they order given name and surname. Respect each culture.
5. Formatting and newlines help readability and to separate distinct pieces of information.
6. The **title** is the most important information and should be highlighted.
7. Publisher organization and location is not relevant, given a resolvable PID.
8. You can cite any publicly available source. It does not have to be peer reviewed—you presumably reviewed the content before citing it?
9. A persistent identifier (PID) or URL MUST be present.
10. Anything cited should be accessible [Open Access](#oa)⁠—[request](#request-preprint) or [post](#post-preprint) a preprint if not.
11. The bibliography is written primarily for human readers on the Web, not for print in 1960s style.
12. The year of publication should be distinct from date of event.

Traditional bibliography styles (of which there are [plenty](https://www.citethisforme.com/)) have several issues:
1. Unnecessary information that relate to printed press
2. Unnecessary shortening of author names and list, which gives preference to surnames and lead authors.
3. Double-comma lists of Surname, F, Surname, S, et al. are very hard to read.
4. Lack of hyperlinks and persistent identifiers
5. Lack of formatting (e.g. difficult to differentiate title and venue).
6. Lack of details for online resources and standards
7. They assume there is shortage of pages, using acronyms that make them difficult to read.
8. Outdated bibliography managers (e.g. for LaTeX) deliberately mangle and remove information such as DOIs and have poor support for non-printed outputs.


## Journal article {#journal}

Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott, Andrew Lonie, Carole Goble, Michael R. Crusoe (2019):  
[**Sharing interoperable workflow provenance: A review of best practices and their practical application in CWLProv**](https://doi.org/10.1093/gigascience/giz095).  
_GigaScience_ **8**(11):giz095  
<https://doi.org/10.1093/gigascience/giz095>

Notes:
1. First line lists **all** authors with full names as listed within article. No [assumptions](https://www.w3.org/International/questions/qa-personal-names) made about surnames.  
  For initials (e.g. middle name or unknown given name), use full punctuation: "C.J. Tunis". 
2. After last author, add (year) in 4 digits, reflecting official publishing date (which may be before the issue's publication date). Terminated with : and newline.
3. Second line is title in **bold**. Hyperlink to DOI—only if open access. Final period `.` is _not bold_ nor in hyperlink, followed by newline.  
  If the landing page for a DOI does not show the full text, the hyperlink MAY go directly to HTML and PDF if the URI seem stable.
4. Third line is full journal name in _italics_ with official captitalization. No acronyms, e.g. _~~J Chem Bio~~_ ⟶ _Journal of Chemical Biology_
5. Journal name is immediately followed by volume number in **bold**. Optional (issue) and/or :article ID. Terminated with newline (no period as there is no sentence). Do not repeat (year) or month of issue, unless this is the official identifier.
6. Page numbers are NOT included⁠—welcome to the Internet.  
  ..except for publications without per-article DOI, then add: pp. 123–129 (that is [en dash](https://en.wikipedia.org/wiki/Dash#Ranges_of_values) –, not _hyphen_ - nor _em dash_ ⁠—)
7. Last line is literal URI, ideally DOI with prefix `https://doi.org/` and any `%2f` within the DOI expanded to `/`
8. Any optional links, e.g. [[preprint](http://example.com/)] or [[poster]](http://example.org/) (see [below](#non-oa))

**Tip**: If you are using Markdown, use two spaces at the end of line to force a `<br />` newline.

## Article/abstract in conference {#in-proceedings}

Kyle Chard, Mike D’ Arcy, Ben Heavner, Ian Foster, Carl Kesselman, Ravi Madduri, Alexis Rodriguez, Stian Soiland-Reyes, Carole Goble, Kristi Clark, Eric W. Deutsch, Ivo Dinov, Nathan Price, Arthur Toga (2016):   
**I’ll Take That to Go: Big Data Bags and Minimal Identifiers for Exchange of Large, Complex Datasets**.  
_IEEE International Conference on Big Data 2016_ ([IEEE BigData 2016](http://cci.drexel.edu/bigdata/bigdata2016/)), 2016-12-05  
<https://doi.org/10.1109/BigData.2016.7840618>
[[preprint]](https://www.research.manchester.ac.uk/portal/en/publications/ill-take-that-to-go-big-data-bags-and-minimal-identifiers-for-exchange-of-large-complex-datasets(8335e672-1d85-4649-a245-56fbdb1bd423).html)

Notes:
1. Conferences are often not consistent in what are their _Full name_, but usually have a consistent (SHRTNAME21).
2. Hyperlink to the conference agenda from the shortname (or full name). As some conferences reuse the same website multiple years, or forget to renew their domain names, archive using Internet Archive's [Wayback Machine](http://web.archive.org/save/) (tip: "Save outlinks" will on a good day archive the proceeding PDFs)
3. Conferences sometimes don't publish proceedings, or publish them a long time after, which could cause (year) to flip over
4. For some reason many conferences still do not publish Open Access. The biggest hint of paywalled conference content is _Springer Lecture Notes_... Make sure you add/ask for a [preprint].
5. If the article is available as a PDF, but without a DOI, the URL may not survive the test of time. Archive specifically with [Wayback Machine](http://web.archive.org/save/).


## W3C Standards {#w3c}

Luc Moreau, Paolo Missier (eds.), Khalid Belhajjame, Reza B'Far, James Cheney, Sam Coppens, Stephen Cresswell, Yolanda Gil, Paul Groth, Graham Klyne, Timothy Lebo, Jim McCusker, Simon Miles, James Myers, Satya Sahoo, Curt Tilmes (2013):  
[**PROV-DM: The PROV Data Model**](http://www.w3.org/TR/2013/REC-prov-dm-20130430/).  
W3C Recommendation 30 April 2013, _World Wide Web Consortium_  
<http://www.w3.org/TR/2013/REC-prov-dm-20130430/>

Richard Cyganiak, David Wood, Markus Lanthaler (eds.), RDF Working Group (2014):  
[**RDF 1.1 Concepts and Abstract Syntax**](http://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/).  
W3C Recommendation 25 February 2014,  _World Wide Web Consortium_  
<http://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/>

Notes:
1. Use the _This Version_ versioned permalink. (Note: these are traditionally `http://` even if they redirect to `https://`) 
2. Editors are listed _first_ unless they are also in the author list. Some specifications don't list authors, in which case you can add the working group, e.g.: RDF Working Group
3. Include the document type and state as shown literally below title, e.g.: W3C Candidate Recommendation 05 March 2020
4. For recommendations published only informally (e.g. `github.io` editor drafts), cite as a [website](#websites).


## RFCs and Internet Drafts {#rfc}

John A. Kunze, Justin Littman, Liz Madden, John Scancella, Chris Adams
J. Kunze, J. Littman, E. Madden, J. Scancella, C. Adams (2018):  
[**The BagIt File Packaging Format (V1.0)**](https://www.rfc-editor.org/rfc/rfc8493.html).  
Request for Comments RFC 8493, _RFC Editor_
<https://doi.org/10.17487/RFC8493>

Stian Soiland-Reyes, Marcos Cáceres (2018):  
[**The Archive and Package (arcp) URI scheme**](https://datatracker.ietf.org/doc/html/draft-soilandreyes-arcp-03).  
Internet-Draft draft-soilandreyes-arcp-03, _Internet Engineering Task Force_  
<https://datatracker.ietf.org/doc/html/draft-soilandreyes-arcp-03>

Tips: 

1. Use <https://datatracker.ietf.org/> to find the latest version and full author names under _Bibtex_ link
2. For Internet-Drafts, cite the versioned identifier, e.g. draft-soilandreyes-arcp-03


## Websites and blogs {#websites}

Cameron Neylon (2017):  
[**As a researcher…I’m a bit bloody fed up with Data Management**](https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/).  
_Science In The Open_ (2017-07-16)  
<https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/> [accessed 2021-12-23](http://web.archive.org/web/20211216094140/https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/)


Tips:
1. You may have to do some research to find the full name of the author(s)
2. Inlude full date in [ISO-8601 format](http://www.w3.org/TR/1998/NOTE-datetime-19980827). You may have to use `curl -I` or _View Source_ to find the publication date. 
3. Visit the front page to find the title of the blog/website. Fallback: Company name or domain name _cameronneylon.net_
4. Make sure the URL does not include unnecessary ?tracker=1234 info.
5. Archive using [WayBack Machine](http://web.archive.org/) and link to snapshotas  [accessed 2021-12-23](http://web.archive.org/web/20211216094140/https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/)


## Personal Communication {#personal}

Personal communication is now easier to cite, thanks to social media and forums. 

Stian Soiland-Reyes (2020):  
[**I am looking for which bioinformatics journals encourage authors to submit their code/pipeline/workflow supporting data analysis**](https://twitter.com/soilandreyes/status/1250721245622079488).  
_Twitter_ (2020-04-16)  
<https://twitter.com/soilandreyes/status/1250721245622079488>

Gurvesh Sanghera (2021):  
[**Guide to run CUDA + WSL + Docker with latest versions (21382 Windows build + 470.14 Nvidia)**](https://forums.developer.nvidia.com/t/guide-to-run-cuda-wsl-docker-with-latest-versions-21382-windows-build-470-14-nvidia/178365).  
_NVidia Forums_ (2021-05-19)  
<https://forums.developer.nvidia.com/t/guide-to-run-cuda-wsl-docker-with-latest-versions-21382-windows-build-470-14-nvidia/178365>


Tips:
1. Social media commonly let you hover over ambigious times like "Yesterday" to reveal the exact timestamp
2. Find "Share" permalinks to make sure you don't use URLs that only work for your account
3. Archive using [WayBack Machine](http://web.archive.org/) if the communication is publicly accessible. 
4. For replies within a thread, use "Inspect Element" to find `id="anchors"` to append as `#anchors` in URI

## Software

Resolution order for how to cite software: 
1. If they have a [CITATION.cff](https://citation-file-format.github.io/) files in a GitHub repository, click _Cite this repository_ to find full list of authors
2. Cite [Journal of Open Source Software](https://joss.theoj.org/) article if present. Search also relevant [software journals](https://www.software.ac.uk/which-journals-should-i-publish-my-software).
3. Use [Zenodo DOIs for Software Release](https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content) if available.  
  Use the version-specific DOI if you used the software, or version-independent "Cite All Versions" DOI if you just reference the software.
4. Cite their "Preferred citation" traditional [journal](#journal) article if website/repo indicates so. You may need to cite the (typically newer) release separately.
5. Cite their main [website](#website). Make sure you find the page most specific to the software.
6. Cite their open source repository 
7. Sorry, if it's not publicly available or documented, I am not sure why you want to cite it!


## Open Access by default {#oa}

s11 strive to publish as [Open
Access](https://www.library.manchester.ac.uk/using-the-library/staff/research/open-research/access/)
(OA), or to provide [Green Open access](https://www.library.manchester.ac.uk/using-the-library/staff/research/open-research/access/understanding/)
preprints where gold open access is not possible. 

Likewise, in this style guide for citations, all bibliographic entries cited
SHOULD be Open Access or otherwise MUST provide an alternative link to a Green
Open Access preprint.


Check: 
* Confirm that accessing the DOI gives an Open Access version of the article. You may have to click "PDF" or similar to find full text.
* Ensure you don't just have accidental institutional access, e.g. by using a Private Browser Window connected with your home ISP
* Check on <https://scholar.google.com/> you are citing the latest version - e.g. a bioRxiv preprint may have a later Open Access journal article with DOI.


### Article that is not Open Access {#non-oa}

If the DOI for a citation do not resolve to an Open Access article, then add
links to a `[preprint]` immediately after DOI:

Sean Bechhofer, Iain Buchan, David De Roure, Paolo Missier, John Ainsworth, Jiten Bhagat, Phillip Couch, Don Cruickshank, Mark Delderfield, Ian Dunlop, Matthew Gamble, Danius Michaelides, Stuart Owen, David Newman, Shoaib Sufi, Carole Goble (2013):  
**Why Linked Data is Not Enough for Scientists**.  
_Future Generation Computer Systems_ **29**(2)
<https://doi.org/10.1016/j.future.2011.08.004> [[preprint](http://users.ox.ac.uk/~oerc0033/preprints/research-objects.pdf)] 

The preprint link should go to, in order of preference:

1. Preprint server like [arXiv](https://arxiv.org/), [bioRxiv](https://www.biorxiv.org/), linking to their landing page rather than PDF, e.g. [arXiv:1310.6555](https://arxiv.org/abs/1310.6555)
2. Funder-supported preprint repository like [Pubmed PMC](https://www.ncbi.nlm.nih.gov/pmc/) or [Europe PMC](https://europepmc.org/), linking to their landing page **if full text is available**, e.g. [PMC2771753](https://identifiers.org/pmc/PMC2771753)
2. Public Repository like [Zenodo](https://zenodo.org/), linking to their landing page (preferably by repository's DOI),  e.g. [[preprint](https://zenodo.org/record/820878))
3. Institutional repository by one of the authors, linking to their landing page, e.g. [[preprint](https://www.research.manchester.ac.uk/portal/en/publications/ill-take-that-to-go(8335e672-1d85-4649-a245-56fbdb1bd423).html)]
4. PDF on conference/journal home page, e.g. [[preprint](http://www.semantic-web-journal.net/content/enhancing-virtual-ontology-based-access-over-tabular-data-morph-csv-0)
5. PDF on author/project home page, e.g. [[preprint](http://users.ox.ac.uk/~oerc0033/preprints/research-objects.pdf)]
6. ResearchGate – only if full text is already uploaded by author!
7. [Wayback Machine](http://web.archive.org/) archive of PDF previously found on above URLs

Tips: 
* Use <https://unpaywall.org/> and <https://scholar.google.com/> to find preprint versions.
* Do not link to Sci-Hub!
* Do not link to publisher PDFs at unaffiliated websites
* Only link to the preprint from the **title** if it is word-for-word equal to the paywalled version and references the published DOI. Otherwise leave title as plain text so readers can choose version.
* Some article templates like IEEE will insert publisher copyright even in author's version. If the DOI and journal issue is clearly missing, it is most likely the author's version and not publisher's version. Likewise, if they are both present it is likely the publisher's version.
* Archive non-DOI PDFs and their landing page using "Save Page Now" on [WayBack Machine](http://web.archive.org/) as websites are likely to change/break/disappear.
* PubMed has both PMID and PMCID identifiers, prefer [PMCID identifiers](https://registry.identifiers.org/registry/pmc) when available, e.g. <https://identifiers.org/pmc/PMC2771753>

Notes:
1. `[preprint]` may be replaced with hyperlinked preprint PIDs without [brackets], e.g. [arXiv:2006.08589](https://arxiv.org/abs/1310.6555) or [PMC2771753](https://identifiers.org/pmc/PMC2771753)
2. Use the the commonly recognized term _preprint_ even if the link technically goes to a later _author-accepted version_ or _postprint_. 
3. If the link goes to a author-hosted PDF that is clearly the publisher's version (technically not open access, but often allowed on author's own site), then the link is called `[pdf]`.


### Posting your own preprint {#post-preprint}

If you are citing one of your own articles, you are responsible to make sure it
is accessible Open Access!

If the article is yours (or you are the co-author), then you can usually post a
preprint yourself on your institutional repository.  Check in JISC's [Sherpa
Romeo](https://v2.sherpa.ac.uk/romeo/) for journal preprint policies. 

For conference submissions where you never signed away a copyright assignment
you always have permission. Note that while a conference may have published
your PDF on the web, conference websites are notoriously poorly maintained and
not likely to remain available in 1, 2, 5, 10 years time.

Posting of preprints should follow the same preferences as above, but check the
publisher's guidelines if you have already signed copyright assignment. The
best is to post the preprint before such signature.

Recommendations:

* Post preprint to [Zenodo](https://zenodo.org/) at submission time, before any copyright assignment. This is useful to get DOI for citing before publishing.
* Post preprint to institutional repository (e.g. <https://pure.manchester.ac.uk/>) at submission time. This is useful for REF acceptance, as a legal backup, and as a way to gather forward links to later versions.
* When accepted, update records in Zenodo and institutional repository. Check preprint policy of publisher if you are allowed to update preprint with the author-accepted version if changed following peer-review/editorial changes.
* When accepted, list paper in personal/project/group bibliography. 
* When published, update all the above. If Gold OA you also have permission to re-publish the publisher's version.
* Add publisher's DOI and journal details to Zenodo and institutional repository metadata.


### Requesting preprint {#request-preprint}

If no preprint is available, then contact authors to request one. Make sure you
don't request a PDF for yourself, but a web-hosted preprint you can link to.

Example request:

> I found your paper "A systematic review of foo bars"
> <https://doi.org/10.13003/abcd>
> which I quite enjoyed and want to cite.
> 
> I have/haven't got access myself, but hope for a Green Open Access 
> URL so that readers of our website/paper can also access your article.
> 
> Are you able to deposit an article preprint or postprint that 
> I can link to from our website/paper?
> 
> For reference, IEEE's preprint policies:
> https://www.ieee.org/publications_standards/publications/rights/authorrightsresponsibilities.html

Include link to the preprint policies of the particular publisher. If they
respond just with a PDF attachment or question of repository, you can recommend
arxiv.org, Zenodo or their institutional repository. 

**Note: You are not allowed to post their preprint yourself, unless you are one
of the co-authors or acting on their behalf in the same copyright holding
institution.**


### Article without preprint

The first preference if the authors are unable to provide an Open Access preprint is **do not cite** the article!

However in some cases the article is fundamental and still needs to be cited. As a last resort, list it with a strong disclaimer about lack of Open Access:

Richard L. Grimsdale, Frank H. Sumner, C.J. Tunis, Tom Kilburn (1959):  
**A system for the automatic recognition of patterns**.  
_Proceedings of the IEE - Part B: Radio and Electronic Engineering_ **106**(26)  
<https://doi.org/10.1049/pi-b-1.1959.0392> (**No Open Access version available**)
