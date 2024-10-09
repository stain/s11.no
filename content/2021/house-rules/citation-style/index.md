---
title: s11 Citation & Bibliography Style Guide
tags:
  - academic
  - citation
summary: >
  The s11 House Rules recommend this opinionated bibliography style for academic writing.

---

In academic writing, the s11 House Rules recommend the following bibliography style:

First Author, Second Author, All Authors (year):  
[**Title**](https://doi.org/10.1000/123456).  
Event/Report, _Venue_ **volume**(issue)  
<https://doi.org/10.1000/123456>

For examples of the s11 bibliography style in use, see most of the [publications](/2022/publications/) and [PhD references](/2023/phd/references/) ([as PDF](https://s11.no/2023/phd/thesis.pdf#section*.92)).

Rationale:
1. It should be possible to write the reference without a bibliography manager (e.g. in Google Docs).
2. All authors SHOULD be credited. We have enough bytes left on the Internet, and _et al._ have high enough h-index already.
3. [Names around the world](https://www.w3.org/International/questions/qa-personal-names) vary in how they order given name and surname, if they even have that concept. Respect each culture and don't reshuffle name parts.
5. Formatting and newlines help readability and to separate distinct pieces of information.
6. The **title** is the most important information and should be highlighted, clearly different from author list or way of publishing.
7. Publisher organization and location is not relevant, given a resolvable PID.
8. You can cite any publicly available source. It does not have to be peer reviewed—you presumably reviewed the content before citing it?
9. A persistent identifier (PID) or URL MUST be present. DOIs are included for _any_ type of resource, where known.
10. Anything cited should be accessible [Open Access](#oa)⁠—[request](#request-preprint) or [post](#post-preprint) a preprint if not.
11. The bibliography is written primarily for human readers on the Web, not for print in 1960s style.
12. The year of publication should be distinct from date of event.

Traditional bibliography styles (of which there are [plenty](https://www.citethisforme.com/)) have several issues:
1. Unnecessary information that only relate to printed press.
2. Unnecessary shortening of author names and author list, which gives preference to surnames and lead authors.
3. Double-comma lists of _Surname, F, Surname, S, et al._ are very hard to read. 
4. Finishing author list with the word _and_ unncessarily emphasizes last author (articles should instead annotate [contributor roles](https://casrai.org/credit/)).
5. Unnecessary abbreviation of journal names (_Future Gener Comp Sy_, _New Engl J Med_) is cryptic and assumes journal is well known to all readers.
6. Unnecessary inclusion of page numbers which are then somehow mangled for continuations to save two bytes -- did you really flip through physical pages 1213--20?
6. Lack of hyperlinks[^1] and persistent identifiers (e.g. DOI) makes it hard to navigate to the publication or to generate consistent metrics. 
7. Lack of formatting (e.g. difficult to differentiate authors, title or venue).
8. Lack of findability details for online resources and standards. Readers should not need to Google the reference and hope for the best!
9. Traditional style assume there is shortage of letters, using acrnms mke it dffclt to read. There are now sufficient spare pages on the Internet.
10. Outdated bibliography managers (e.g. for LaTeX) deliberately mangle and remove information such as DOIs in order to emulate 1960s printing press practices.
11. Bibliography manager outputs can't easily be edited when the journal's style is outdated or misleading. For instance, showing a temporary URL to a journal website from the `url` BibTeX field and ignoring the `doi` field.
12. Bibliography managers have poor support for modern scholarly outputs, as they assume authors only cite outputs from a printing press. This makes it hard to cite software, websites, online proceedings.

The s11 bibliography style can be considered as a combination of these citation styles:
* [ACM SIGCHI Proceedings](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Facm-sigchi-proceedings) (Full names, year, journal in italics) -- title is distinct but could be emphasized more. 
* [American Sociological Association (ASA)](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Famerican-sociological-association) (full names, year, journal in italics, distinct title) -- but first author is in wrong order and adds a confusing comma, no DOIs
* [Association for Computing Machinery](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Fassociation-for-computing-machinery) (Full names, year, journal in itailcs) -- but journals are abbreviated, unnecessary "DOI" prefix, year with full stop is odd sentence, "and" in author list requires Oxford Comma considerations.
* [IOS Press (books)](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Fios-press-books) (journal issue in bold) -- but DOIs don't have `https://doi.org/` prefix, abbreviated journals, indistinct title
* [Cambridge University Press](https://editor.citationstyles.org/styleInfo/?styleId=http%3A%2F%2Fwww.zotero.org%2Fstyles%2Fcambridge-university-press-numeric) (journal in italics, journal volume is bold) -- but comma after authors might make title seem like author ("I. Mares, Firms and the welfare state"), Oxford Comma before `&` is odd


[^1]: Although use of footnotes for URLs is easy to navigate (if hyperlinked!), used alone they also degrade Web resources as not being "proper" publications worthy of attribution and citation. 

## s11 Citation Style Language

An experimental [CSL](https://citationstyles.org/) definition [s11.csl](s11.csl) is available, but may require
some final editing. [Contributions welcome!](https://github.com/stain/s11.no/blob/main/content/2021/house-rules/citation-style/s11.csl).

Example usage with [pandoc](https://pandoc.org/):

```shell
$ pandoc -i original.tex --wrap=preserve \
  --bibliography references.bib \
  --csl https://s11.no/2021/house-rules/s11-citation-style.csl \
  -t gfm -o index.md
```


## Journal article {#journal}

Farah Zaib Khan, Stian Soiland-Reyes, Richard O. Sinnott, Andrew Lonie, Carole Goble, Michael R. Crusoe (2019):  
[**Sharing interoperable workflow provenance**: A review of best practices and their practical application in CWLProv](https://doi.org/10.1093/gigascience/giz095).  
_GigaScience_ **8**(11):giz095  
<https://doi.org/10.1093/gigascience/giz095>

Notes:
1. First line lists **all** authors with full names as, listed within article. No [assumptions](https://www.w3.org/International/questions/qa-personal-names) made about surnames.  
  For initials (e.g. middle name or unknown given name), use full punctuation: "C.J. Tunis".   
  Respect author's (possibly mixed) culture and language, and their preferred (academic) name, for instance "Bruno de Paula Kinoshita",  "José Mª Fernández", "Karsten Peters-von Gehlen".  
  Use the latin alphabet (possibly transcribed), but preserve accents, for instance "Matúš Kalaš".  
  **Tip**: Sadly many journals now make it hard to copy/paste author names, shorten long list of authors, Springer sometimes reorders authors(!), some embed graphics with `ORCID` alt texts -- use <https://search.crossref.org/> to find the full author names as registered for a DOI.
2. Names are listed with regular comma `,` as separator, including for last name. No need for `et al.`, `and` or `&`. First author is listed by full name without re-arranging for Westernsurname,Givenname.
3. After last author, add (year) in 4 digits, reflecting official publishing date (which may be before the issue's publication date). Terminated with : and newline.
4. Second line is title in **bold**. Hyperlink title to DOI—only if open access.  
  If the title has two sentences or a clause separated by `:` or -- (as above), only use bold on first half, but hyperlink full title. Do not split formatting if the first half is a single word or product name alone.
  Final period `.` is _not bold_ nor in hyperlink (drop `.` if title ends with a symbol like `!`). Terminate with newline.  
  If the landing page for a DOI does not show the full text, the hyperlink MAY go directly to HTML and PDF if the URI seem stable and it renders in browser rather than download.
5. Third line is full journal name in _italics_ with official captitalization. No acronyms, e.g. _~~J Chem Bio~~_ ⟶ _Journal of Chemical Biology_  
  **Tip**: Many journals for some reason don't list their own name as copy--pasteable text ([xkcd:773](https://xkcd.com/773/)), use <https://search.crossref.org/> to check.
6. Journal name is immediately followed by volume number in **bold**. Optional (issue) and/or :article ID. 
  Terminated with newline (no period as there is no sentence). Do not repeat (year) or month of issue, unless this is the official identifier.
7. Page numbers are **not** included⁠—welcome to the Internet.  
  ..except for publications without per-article DOI (one large PDF), then add: pp. 123–129 (that is [en dash](https://en.wikipedia.org/wiki/Dash#Ranges_of_values) –, not _hyphen_ - nor _em dash_ ⁠—)
8. Last line is literal URI, ideally DOI with prefix `https://doi.org/` and any `%2f` within the DOI expanded to `/`
9. Any optional links, e.g. [[preprint](http://example.com/)] or [[poster]](http://example.org/) (see [below](#non-oa))

**Tip**: If you are using Markdown, use two spaces `  ` or `\` at the end of line to force a `<br />` newline. Below is a Markdown template:

```markdown
G S (2000):  
[**T**](d).  
_J_ **v**(i):a  
<d>
```


## Article/abstract in conference {#in-proceedings}

Kyle Chard, Mike D’ Arcy, Ben Heavner, Ian Foster, Carl Kesselman, Ravi Madduri, Alexis Rodriguez, Stian Soiland-Reyes, Carole Goble, Kristi Clark, Eric W. Deutsch, Ivo Dinov, Nathan Price, Arthur Toga (2016):   
**I’ll Take That to Go**: Big Data Bags and Minimal Identifiers for Exchange of Large, Complex Datasets.  
_IEEE International Conference on Big Data 2016_ ([IEEE BigData 2016](http://cci.drexel.edu/bigdata/bigdata2016/)), Washington DC, USA, 2016-12-05  
<https://doi.org/10.1109/BigData.2016.7840618>
[[preprint]](https://www.research.manchester.ac.uk/portal/en/publications/ill-take-that-to-go-big-data-bags-and-minimal-identifiers-for-exchange-of-large-complex-datasets(8335e672-1d85-4649-a245-56fbdb1bd423).html)

Alasdair Gray, Carole Goble, Rafael Jimenez, Bioschemas Community (2017):\
[**Bioschemas: From Potato Salad to Protein Annotation**](https://ceur-ws.org/Vol-1963/paper579.pdf).\
*Proceedings of the ISWC 2017 posters & demonstrations and industry
tracks co-located with 16th international semantic web conference* ([ISWC 2017](https://web.archive.org/web/20180723152956/https://iswc2017.semanticweb.org/)), Vienna, Austria.\
*CEUR Workshop Proceedings* **1963**\
<https://iswc2017.semanticweb.org/paper-579/>  
<https://ceur-ws.org/Vol-1963/paper579.pdf>


Notes:
1. Conferences are often not consistent in what are their _Full name_, but usually have a consistent (SHRTNAME21). Do not italics the shortname as it's not part of the full name.
2. If the conference has already published proceedings, then prefer the _book title_ (typically _Proceedings of the 5th International ..._) rather than the conference website name. Do _not_ include the editors of the proceedings (unless citing the whole of proceedings). 
3. Hyperlink to the conference/agenda from the shortname (or full name). As some conferences reuse the same website multiple years, or forget to renew their domain names, archive using Internet Archive's [Wayback Machine](http://web.archive.org/save/) (tip: "Save outlinks" will on a good day archive the proceeding PDFs)
4. Conferences sometimes don't publish proceedings, or publish them a long time after, which could cause the published (year) to flip over. Optionally include the conference date in ISO-8601 format, it may differ from the published year. If a conference was delayed (e.g. in COVID-19 lockdown) then the shortname year may not match the conference dates.
5. For some reason many conferences still do not publish Open Access. The biggest hint of paywalled conference content in my field is _IEEE_ or _Springer Lecture Notes_... Make sure you add/ask for a [preprint].
6. Do _not_ include the publisher name (e.g. Springer). Do include publisher's proceeding series (_Lecture Notes in Computer Science_ **13373**) on a separate name.
7. If the article is available as a PDF, but without a DOI, the URL may not survive the test of time. Archive specifically with [Wayback Machine](http://web.archive.org/save/).
8. You may need to include multiple URLs, e.g. the conference lists the abstract and links to video, while the 
9. Some citation software and websites may confusingly list the city of the proceeding publisher's head quarters (e.g. Springer, New York, NY) instead of where the conference actually took place. If in doubt, remove the location, it is seldom relevant for international conferences. Some conferences are also online/hybrid.

## Books and chapters {#books}

Lois Mai Chan (1995):  
**Library of Congress Subject Headings: Principles and Application**, 3rd edition.   
[ISBN 9781563081910](https://identifiers.org/isbn/9781563081910).

Barend Mons (2018):\
**Data Stewardship for Open Science**.\
[ISBN 9781315351148](https://identifiers.org/isbn/9781315351148)

William Stallings (1990):\
**Handbook of computer-communications standards: The open systems (OSI)
model and OSI-related standards**, 2nd ed.\
Sams.\
[ISBN 978-0-672-22697-7](https://identifiers.org/isbn/9780672226977)

Tim Berners-Lee, Mark Fischetti (1999):\
**Weaving the Web**: The original design and ultimate destiny of the World Wide Web by its inventor.\
[ISBN 978-0-06-251586-5](https://identifiers.org/isbn/9780062515865)

Christian Bizer, Tom Heath, Tim Berners-Lee (2011):\
**Linked data: The story so far**.\
*Semantic Services, Interoperability and Web Applications: Emerging Concepts*, Amit Sheth (ed.)  
[ISBN 9781609605933](https://identifiers.org/isbn/9781609605933)
<https://doi.org/10.4018/978-1-60960-593-3.ch008>

Luiz Olavo Bonino Da Silva Santos, Mark D. Wilkinson, Arnold Kuzniar,
Rajaram Kaliyaperumal, Mark Thompson, Michel Dumontier, Kees Burger
(2016):\
**FAIR Data points supporting big data interoperability**.\
*Enterprise interoperability in the digitized and networked factory of
the future*, Martin Zelm, Guy Doumeingts, Joao Pedro Mendonça (eds.).\
iSTE Press.\
[ISBN 978-1-84704-044-2](http://www.iste.co.uk/book.php?id=1073)\
[[preprint](https://www.researchgate.net/publication/309468587_FAIR_Data_Points_Supporting_Big_Data_Interoperability)]

1. Split the title as for journal articles, unless the first part indicates the book series (see examples above)
1. Check carefully if the book is actually a conference [proceeding]({#in-proceedings}). You may need to navigate to the cover/introduction chapter.
2. It can be hard to find preprints of text books, but some authors publish green open access versions of their book chapters. 
3. Include the ISBN number if known. Prefer the "electronic" issue. Use `https://identifiers.org/isbn/` as prefix, removing any `-` and prefix `978` on shorter ISBN-10. Report any unknown ISBN to the resolver  (instead link the ISBN to the publisher's page as in iSTE example above).
4. Cite as well the DOI of the book if available.
4. Check you are citing the right (typically latest) edition -- editors/authors may change.
5. You may include the publisher name, particularly if there is no ISBN. 
6. Do not include the publisher's address/city -- no-one will go visit them.
7. Include publisher name for older books which may not have an online landing page or ISBN.
8. If citing a chapter, use **chapter title** and _book title_ similiar to as in [proceeding]({#in-proceedings}); include editors unless equal to authors. You don't need to include "In: " due to the use of italics.


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
[**The BagIt File Packaging Format** (V1.0)](https://www.rfc-editor.org/rfc/rfc8493.html).  
Request for Comments RFC 8493, _RFC Editor_  
<https://doi.org/10.17487/RFC8493>

Stian Soiland-Reyes, Marcos Cáceres (2018):  
[**The Archive and Package (arcp) URI scheme**](https://datatracker.ietf.org/doc/html/draft-soilandreyes-arcp-03).  
Internet-Draft draft-soilandreyes-arcp-03, _Internet Engineering Task Force_  
<https://datatracker.ietf.org/doc/html/draft-soilandreyes-arcp-03>

Tips: 

1. Use <https://datatracker.ietf.org/> to find the latest version, HTML link and full author names under _Bibtex_ link
2. For Internet-Drafts, cite the versioned identifier, e.g. draft-soilandreyes-arcp-03


## IEEE standards

Raja Mazumder, Vahan Simonyan (eds.) (2020):\
**IEEE Standard for Bioinformatics Analyses Generated by High-Throughput
Sequencing (HTS) to Facilitate Communication** (2020).\
*IEEE Std* **2791-2020**.\
ISBN 978-1-5044-6466-6.\
<https://research.manchester.ac.uk/en/publications/936de52b-ac53-4f0e-9927-77fd7073e88d>\
<https://doi.org/10.1109/ieeestd.2020.9094416>


1. To find the title, editors and/or working group, search in [standards.ieee.org](https://standards.ieee.org/)
2. Use [IEEE Explore](https://ieeexplore.ieee.org/browse/standards/collection/ieee) to find the DOI for the standard -- this may appear later for new standards.
3. It can be hard to find preprints of EEE standards. 

## ISO standards

ISO/IEC (2022):  
**ISO/IEC 23009-1:2022 — information technology — dynamic adaptive streaming over HTTP (DASH) — part 1: Media presentation description and segment formats**.  
ISO standard  
<https://www.iso.org/standard/83314.html>

1. ISO standards may have multiple standard bodies, e.g. "ISO/IEC" above.
2. ISO standards don't tend to have DOIs or ISBN. Why should a standard body use standard identifiers?
3. Locate it from <https://www.iso.org/standards.html> -- make sure to find the correct _part_ and _year_. You can normally see a preview. Note that the number in the `standard/` URI do _not_ match the ISO standard number!  
 Do _not_ link to the [Online Browsing platform](https://www.iso.org/obp/ui/en/#iso:std:iso-iec:23009:-1:ed-5:v1:en), 


## Websites and blogs {#websites}

Cameron Neylon (2017):  
[**As a researcher…I’m a bit bloody fed up with Data Management**](https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/).  
_Science In The Open_ (2017-07-16)  
<https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/> [[accessed 2021-12-23](http://web.archive.org/web/20211216094140/https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/)]


Tips:
1. You may have to do some research to find the full name of the author(s). Use the website name if unknown.
2. Include full date in [ISO-8601 format](http://www.w3.org/TR/1998/NOTE-datetime-19980827). You may have to use `curl -I` or _View Source_ to find the publication date. 
3. Visit the front page to find the title of the blog/website. Fallback: Company name or domain name _cameronneylon.net_
4. Make sure the URL does not include unnecessary ?tracker=1234 info.
5. Archive using [WayBack Machine](http://web.archive.org/) and link to snapshot, e.g.  [[accessed 2021-12-23](http://web.archive.org/web/20211216094140/https://cameronneylon.net/blog/as-a-researcher-im-a-bit-bloody-fed-up-with-data-management/)]  
  (Particularly when updating a preprint), if the link has already rotten (404 Not Found, domain squatters, server error), cross out the URL ~~<http://example.com/>~~ and add closest web archive link [[archived 2021-11-21](http://web.archive.org/web/20211216093718/https://example.com/)] 


## Personal Communication {#personal}

Personal communication is now easier to cite, thanks to social media and forums. 

Stian Soiland-Reyes (2022):  
[**I deleted my Twitter account…**]().  
_scholar.social_, Mastodon (2023-09-19)  
<https://scholar.social/@soilandreyes/111093469588864194>
[[archived 2023-09-19](https://web.archive.org/web/20230919215831/https://scholar.social/@soilandreyes/111093469588864194)]

Stian Soiland-Reyes (2020):  
[**I am looking for which bioinformatics journals encourage authors to submit their code/pipeline/workflow supporting data analysis**](https://twitter.com/soilandreyes/status/1250721245622079488).  
_Twitter_ (2020-04-16)  
<https://twitter.com/soilandreyes/status/1250721245622079488>
[[archived 2021-05-05](https://web.archive.org/web/20210504092435/https://twitter.com/soilandreyes/status/1250721245622079488)]

Gurvesh Sanghera (2021):  
[**Guide to run CUDA + WSL + Docker with latest versions (21382 Windows build + 470.14 Nvidia)**](https://forums.developer.nvidia.com/t/guide-to-run-cuda-wsl-docker-with-latest-versions-21382-windows-build-470-14-nvidia/178365).  
_NVidia Forums_ (2021-05-19)  
<https://forums.developer.nvidia.com/t/guide-to-run-cuda-wsl-docker-with-latest-versions-21382-windows-build-470-14-nvidia/178365>


Tips:
1. Social media commonly let you hover over ambigious times like "Yesterday" to reveal the exact timestamp
2. Find "Share" permalinks to make sure you don't use URLs that only work for your account
3. Archive using [WayBack Machine](http://web.archive.org/) or <https://archive.is/> if the communication is publicly accessible. 
4. For replies within a thread, use "Inspect Element" to find `id="anchors"` to append as `#anchors` in URI
5. Note that some social media may require authentication or otherwise prevent public visibility. Some countries block common social media websites.


## Software

Ghaith Arfaoui, Maroua Jaoua (2020):\
**RO-Crate RDA maDMP Mapper**.\
*Zenodo*\
<https://github.com/GhaithArf/ro-crate-rda-madmp-mapper>\
<https://doi.org/10.5281/zenodo.3922136>

Finn Bacall, Stian Soiland-Reyes, Marina Soares e Silva (2019):\
**eScienceLab: RO-Composer**.\
<https://esciencelab.org.uk/projects/ro-composer/>\
<https://github.com/ResearchObject/research-object-composer>

Kostadin Belchev (2021):\
**KockataEPich/CheckMyCrate: A command line application for validating a
RO-Crate object against a JSON profile**.\
*GitHub*.\
<https://github.com/KockataEPich/CheckMyCrate>

Resolution order for how to cite software: 
1. If they have a [CITATION.cff](https://citation-file-format.github.io/) files in a GitHub repository, click _Cite this repository_ to find full list of authors.
2. Cite [Journal of Open Source Software](https://joss.theoj.org/) article if present. Search also relevant [software journals](https://www.software.ac.uk/which-journals-should-i-publish-my-software).
3. Use [Zenodo DOIs for Software Release](https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content) if available.  
  Use the version-specific DOI if you used the software, or version-independent "Cite All Versions" DOI if you just reference the software.
4. Cite their "Preferred citation" traditional [journal](#journal) article if website/repo indicates so. You may need to cite the (typically newer) release separately.
5. Cite their main [website](#website). Make sure you find the page most specific to the software.
6. Cite their open source repository -- make a snapshot with [Software Heritage](https://archive.softwareheritage.org/) and cite the [SWHID](https://docs.softwareheritage.org/devel/swh-model/persistent-identifiers.html) (which may be made specific for version/filename if desired). For GitHub/GitLab, include `owner/repositoryname` in the title, as some repository names can be overly general.
7. You may find it useful to combine several of the above, note that many journals will mangle this up anyway.
8. Sorry, if it's not publicly available or documented, I am not sure why you want to cite it!

For case 5/6 it can be difficult to find the author names. In some cases there may be an organization that can be listed (including GitHub owner).





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
* Ensure you don't just have accidental institutional access, e.g. by using a Private Browser Window connected with your home ISP.
* Check on <https://scholar.google.com/> you are citing the latest version - e.g. a bioRxiv preprint may have a later Open Access journal article with DOI.


### Article that is not Open Access {#non-oa}

If the DOI for a citation do not resolve to an Open Access article, then add
links to a `[preprint]` immediately after DOI:

Sean Bechhofer, Iain Buchan, David De Roure, Paolo Missier, John Ainsworth, Jiten Bhagat, Phillip Couch, Don Cruickshank, Mark Delderfield, Ian Dunlop, Matthew Gamble, Danius Michaelides, Stuart Owen, David Newman, Shoaib Sufi, Carole Goble (2013):  
**Why Linked Data is Not Enough for Scientists**.  
_Future Generation Computer Systems_ **29**(2)  
<https://doi.org/10.1016/j.future.2011.08.004> [[preprint](http://users.ox.ac.uk/~oerc0033/preprints/research-objects.pdf)] 

The preprint link should go to, in order of preference:

1. Preprint server like [arXiv](https://arxiv.org/), [bioRxiv](https://www.biorxiv.org/), linking to their landing page rather than PDF, e.g. [arXiv:1310.6555](https://arxiv.org/abs/1310.6555). 
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
* Do not link to publisher PDFs at unaffiliated websites (except author's own website which is often permitted)
* Only link to the preprint from the **title** if it is word-for-word equal to the paywalled version and references the published DOI. Otherwise leave title as plain text so readers can choose version.
* Some article templates like IEEE will insert publisher copyright even in author's version (cheeky!). If the DOI and journal issue is clearly missing, it is most likely the author's version and not publisher's version. Likewise, if these are both present, it is likely the publisher's version.
* Archive non-DOI PDFs and their landing page using "Save Page Now" on [WayBack Machine](http://web.archive.org/), as websites and unofficial PDFs are likely to change/break/disappear.  
  **Tip**: Archived PDFs are likely to become indexed on <https://scholar.archive.org/> 
* PubMed has both PMID and PMCID identifiers, prefer [PMCID identifiers](https://registry.identifiers.org/registry/pmc) when available, e.g. <https://identifiers.org/pmc/PMC2771753>

Notes:
1. `[preprint]` may be replaced with hyperlinked preprint PIDs without [brackets], e.g. [arXiv:2006.08589](https://doi.org/10.48550/arXiv.1310.6555) or [PMC2771753](https://identifiers.org/pmc/PMC2771753) -- if the preprint server has a DOI, use that as hyperlink, but do **not** include it as literal DOI unless the journal/proceedings did not itself assign DOIs.
3. Use the commonly recognized term _preprint_ even if the link technically goes to a later _author-accepted version_ or _postprint_. 
4. If the link goes to a author-hosted PDF that is clearly the publisher's version (technically not open access, but often allowed on author's own site), then the link is called `[pdf]`.
5. Even if an article is in arXiv or Pubmed, you should still include the publisher's DOI.


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
best is to post the preprint _before_ such signature.

Recommendations:

* Post preprint to [Zenodo](https://zenodo.org/) at submission time, before any copyright assignment. This is useful to get DOI for citing before publishing.
* Post preprint to institutional repository (e.g. <https://pure.manchester.ac.uk/>) at submission time. This is useful for REF acceptance, as a legal backup, and as a way to gather forward links to later versions. Link to public preprint in Zenodo.
* Now you can cite this preprint in any of your other works that are in preparation. You may not know in advance their order of publication! You may need to update the preprint if you create circular citations.
* When accepted, update records in Zenodo and institutional repository. Check preprint policy of publisher if you are allowed to update preprint with the author-accepted version if changed following peer-review/editorial changes.
* When accepted, list paper in personal/project/group bibliography. 
* When published, update all the above. If Gold/Diamond OA you also have permission to re-publish the publisher's version, so why not!
  **Note**: Even if published as "Open" Access, some publishers like Oxford University Press may add "Are you a human" checks, advertisements and pop-ups. Some hybrid journals may randomly flip your article back into paywalled mode by accident. Always archive the final PDF in your institutional repository -- it may even be indexed by <https://scholar.google.com/> !
* Add publisher's DOI and journal details to Zenodo and institutional repository metadata.
* Update citations in other in-flight publications that previously cited the preprint (e.g. minor revisions). Do it **now** so you don't forget, even if their review is not back!


### Requesting preprint {#request-preprint}

If no preprint is available, then contact authors to request one. Make sure you
don't request a PDF for yourself, but a web-hosted preprint you can link to,
solving the access problem for the world instead of just you, as you typically
do _not_ have permission to re-share emailed PDFs.

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

You may include link to the preprint policies of the particular publisher. If
they respond just with a PDF attachment or question of repository, you can
recommend arxiv.org, Zenodo or their institutional repository. 

**Note: You are not allowed to post their preprint yourself, unless you are one
of the co-authors or acting on their behalf in the same copyright holding
institution.**


### Article without preprint

The first preference if the authors are unable to provide an Open Access preprint is **do not cite** the article! The radical rationale for this is: if the author didn't want anyone to read it, why should you cite it?

However in some cases the article is fundamental and still needs to be cited. As a last resort, list it with a strong disclaimer about lack of Open Access:

Richard L. Grimsdale, Frank H. Sumner, C.J. Tunis, Tom Kilburn (1959):  
**A system for the automatic recognition of patterns**.  
_Proceedings of the IEE - Part B: Radio and Electronic Engineering_ **106**(26)  
<https://doi.org/10.1049/pi-b-1.1959.0392> (**No Open Access version available**)


## Inline citations and bibliography

For preparing a preprint or initial submission for a journal or conference,
consider the usability of the references for the reader or reviewer, rather
than poor publisher/Overleaf templates.

If a manuscript is being prepared in a collaborative environment like Google
Docs, or will be [published on the Web](/2022/publications/), or in another
system with a poor bibliographical manager, then use inline
citations with hyperlinks to the DOI:

<div style="margin-left: 4em">

However, in this accelerated ecosystem of Open Science, concerns have been raised about replicability of research findings [[Ioannidis 2005](https://doi.org/10.1371/journal.pmed.1004085)], flagged as a “reproducibility crisis” [[Baker 2016](https://doi.org/10.1038/533452a)].

</div>

In the bibliography, list by including the [key] before the full name listing:

##### References

[Baker 2013] Thomas Baker, Sean Bechhofer, Antoine Isaacc, Alistair Miles, Guus Schreiber, Ed Summers (2013):  
**Key choices in the design of Simple Knowledge Organization System** (SKOS).
_Journal of Web Semantics_ **20**  
<https://doi.org/10.1016/j.websem.2013.05.001>

[Baker 2016] Monya Baker (2016):  
**1,500 scientists lift the lid on reproducibility**.  
_Nature_ **533**  
<https://doi.org/10.1038/533452a>

[Ioannidis 2005] John P. A. Ioannidis (2005):  
**Why Most Published Research Findings Are False**.  
_PLOS Medicine_ **19**(8):e1004085  
<https://doi.org/10.1371/journal.pmed.1004085>

[RDF 1.1 2014] RDF Working Group (2014):  
**RDF 1.1 Concepts and Abstract Syntax**.  
_W3C Recommendation_ 25 Feb 2014.  
<https://www.w3.org/TR/2014/REC-rdf11-concepts-20140225/>


1. Avoid using `[14]` style numeric references, as they are meaningless without scrolling to the reference list, which works poorly on screens.
2. Include only the surname of only the first author (you did list all of the full names in the bibliography?).  
   You may need to investigate (e.g. in CrossRef metadata or on the author's ORCID record) which part of the name can be considered the surname. 
3. Include the full surname, with prefixes/accents. You may need to check regional conventions, for instance [Ó Carragáin 2019a] [Van de Sompel 2007] [de Visser 2023] [Nieva de la Hidalga 2021]
3. Do not include `et al.` as most citations would then say that. You may have to bend this rule if one of your co-authors is one of the als.
4. Hyperlink to the DOI or preprint of the article following same rules as for Title above. These are super-useful for your co-authors and reviewers!
5. Add the s11-formatted reference at the end. Not only will your preprint look nice, but you will find later is now very easy to copy/paste into any reference manager!
6. While editing, place references into the bibliography semi-alphabetically according to their key.  
7. Use letters after the year if there's more than one citation with same name and year e.g. [De Geest 2023a]
   Use letters even if it's two different people with the same surname, similar to [Baker 2013] and [Baker 2016] above.
8. To tidy up, sort the references properly, using "line move" function in your editor. Delete no-longer-cited references.  
   For extra OCD points you may check alphabetical sorting rules depending on
   the name's language, for instance Belgian "De Geest" is under D, Dutch "de
   Visser" is under V, Irish "Ó Carragáin" is under C, "Möller" is before "Mons", "Søiland" is after "Syse". Note that some authors like myself may have moved country or have a surname with multiple languages.
9. Renumber any lettered citations to avoid gaps. You may use search--replace through an intermediary "De Geest 2023Xa" if you feel the need to reorder.
10. When the author is an organisation, use their acronym if available, e.g. [W3C 2020] [MDN 2023] 
11. For numbered standards, use their short form e.g. [ISO 23009-1] (exception: RFCs are listed by their first author)
12. Remember, this is a key, not a reference! The full details are listed under your _References_
13. To change keys to a valid bibtex key, simply delete the space.
14. For publishing on the Web, include the **title** of the citation in the hyperlink markup. In Markdown this can be achived using bookmarks, in HTML `<a href="" title="">` 

Markdown example using bookmarks:

```markdown
...code, data formats or software versions [[Stodden 2016]].

[Stodden 2016]: https://doi.org/10.1126/science.aah6168 "Enhancing reproducibility for computational methods"
```

Note that the bookmarks are expanded and not rendered as a list. In reference list you need to escape:

```markdown
\[Stodden 2016\] Victoria Stodden, Marcia McNutt, David H. Bailey, 
Ewa Deelman, Yolanda Gil, Brooks Hanson, Michael A. Heroux, 
John P.A. Ioannidis, Michela Taufer (2016):
```


