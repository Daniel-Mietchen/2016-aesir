Annotation as a service: helping build a global knowledge layer with annotation of the dark literature.
=======================================================================================================

Codename: Aesir.

Abstract:
---------

We propose to build server-side functionality to enable anyone to
consume text and add annotations to it, using the `hypothes.is
annotation system <http://hypothes.is>`__.  This would complement the
client-side manual annotation functionality already offered by
hypothes.is, and enable server-based analysis of private document
collections.  The primary value proposition is to enable deeper
annotation and meta-analysis of a vast range of scientific literature,
including closed-access papers, pre-publication and in-review papers,
"informal" literature such as blog posts and tutorials, software
manuals and documentation, and micro- and meso-scale data resources.
In effect, these annotations would constitute an open metadata layer
across all of science, and usher in a golden age of scientific
communication.

Introduction:
-------------

`Hypothes.is <http://hypothes.is>`__ is an annotation overlay that
allows annotations to be associated with text. Each annotation
consists of a document ID, a document anchor, some free text, and
tags; annotations can be either public or belong to private groups.
The hypothes.is service currently offers an overlay display where
these annotations are placed on HTML or PDF views of
documents. Annotations can be placed manually by means of a Chrome
plugin, or the same code delivered via JavaScript embedding or a Web
proxy.  Annotations are stored in the hypothes.is central database and
can be retrieved on demand for any specified URL, user, group, or
tag. Annotations are searchable along these facets as well as with
free text query.

Hypothes.is offers an optional overlay and enables permissionless
annotation by 3rd parties unaffiliated with either the content
consumer or the content provider.  Crucially, this bypasses much of
the friction associated with working with publishers to provide an
annotation overlay, although a large consortium of publishers *is*
working closely with hypothes.is.

The functionality currently offered by hypothes.is is largely *client
side*, in that most annotations are entered manually.  In many cases,
more automated or deeper computational analysis (e.g. of linguistic
structure, or correlations with existing literature) would be
valuable, and this would require a programmatic interface to entering
annotations.  There is no fundamental technical barrier to
programmatically entering annotations at large scale, and the
ContentMine/Hypothes.is contest entry seeks to implement exactly that,
using ContentMine to extract facts and metadata from the open
literature and then annotate the document with Hypothes.is.
However, there is currently no way to enable automated analysis of
closed or not-yet-public literature.

We therefore propose to build server-side software that would enable
individuals, institutions, and others to provide analysis and
annotation services as a Web service.  The primary client-side
mechanism would be a bookmarklet or in-browser app that would submit
HTML or PDF text to a server for analysis.  On the server side, we
would provide Python libraries for text consumption and normalization,
anchor extraction, annotation retrieval, and annotation submission.
Our ultimate goal is to open up an ecosystem of annotation production,
consumption, and meta-analysis to everyone, and to allow anyone with
access to any document to enter it into this ecosystem.

Three use cases that Aesir would enable
---------------------------------------

1. **Annotating closed literature.** Aeneas is reading a paper from
   2004 on a closed-access site, and is interested in knowing who has
   cited the paper, linking to back references and identifying which
   have been retracted, and seeing what databases have used the
   information from the paper.  Because the paper is not accessible to
   any automated annotation services, none of this information can be
   posted on the paper. Aeneas submits the paper to the Aesir
   annotation server with a click, which annotates it and "paints" the
   paper with annotations.
   
2. **Automating deep annotation of closed literature.** Tina has
   access to an otherwise inaccessible paper, and wants to apply
   `ContentMine <http://contentmine.org/>`__ to it.  She cannot give
   ContentMine direct access to it. Tina submits the paper to an Aesir
   server running ContentMine, which analyzes and annotates the paper.

3. **Leveraging & driving open peer review.** James is reviewing a
   paper, and wants to mark it up with external blog commentary and
   public reviews.  Unfortunately, the paper is a revision of a posted
   preprint and so its hypothes.is URL has changed and no annotations
   are associated with it; James submits the paper to a service that
   identifies it as a duplicate of a previously annotated paper and
   transfers the annotations over to it where possible.  As a bonus,
   James could annotate the paper with his review when he is done.

Why does this fit the Open Science Prize?
-----------------------------------------

We are encouraging and supporting services, tools, and platforms that
enable the generation of open content: here, the comments, extractions,
and annotations on literature.  The proposed system could also consume,
integrate, analyze, and compare *existing* annotations, enabling
**metanalysis** of annotations.  And, since annotations in hypothes.is
are explicitly licensed under CC0, there is no restriction on reuse
or remixing.

Moreover, by hacking the precedent of fair use in using cloud services
to store and search personal document collections (c.f. Evernote and
Papers), we believe we can open up old and closed literature.  The
initial beneficiaries of this will be the closed-access publishers who
may find more users of their closed archives, but even this serves the
greater good by linking this closed literature into the global
annotatome.  In the long term, we believe this will serve as a
powerful demonstration of the uses and power of open literature.

Longer term, we believe there will be many groups interested in
permissionless server-side automated annotation of text, and we hope
that by providing an automated system matching the existing client
annotation interface, we can more readily enable the development of an
ecosystem of approaches to open annotation.

Deliverables
------------

The first line of deliverables would be a full server (implemented in
Python) for adding annotations to documents, together with JavaScript
bookmarklets to enable submission of documents to such servers from
within any modern Web browser.  The server code would contain an open
source implementation of the parsing and annotation-marking logic used
in hypothes.is, providing a framework that would readily enable
developers to consume text and annotate it according to their own
logic.  We would provide a full demo server implementation using a
public open source code base (here, working with ContentMine would be
a natural fit). We would also provide simple hooks to enable anyone
to integrate whatever annotation engine they wanted.

A prototype implementation will be available shortly.

On top of these deliverables we envision a variety of services, depending
on where we opportunities develop:

* large-scale annotation search and comparison, so that documents can
  be grouped and analyzed based on their annotations and larger
  networks of annotations;
   
* enabling human feedback on and editing of automated annotations
  within hypothes.is itself, so that viewers can annotate annotations
  and identify misannotations;
  
* a recommendation system based on annotation similarity and
  interlinking, so that when annotations become dense enough, new
  associates can be found between existing literature;
  
* a notification service that would allow people to "watch"
  collections of annotations and/or publications, and filter the
  notifications;
  
* more advanced annotation overlays for documents;
  
* tools for managing annotations from multiple sources, integrating
  with social information (lab groups, collaborators, institutions),
  and support for trust network overlays;

* unifying scattered versions and representations by marrying
  automatic analysis and human curation; for example, hypothes.is
  could be used to store "document signatures" that could be searched
  to connect papers with different URIs.

Impacts and ecosystem
---------------------

First and foremost, we believe we can enable an ecosystem of annotation
algorithms, some general (e.g. linguistic analysis of document
structure) and some field-specific (e.g. automated extraction and
annotation of drug-drug interactions across document collections).

Second, we envision this as providing entree to the "dark
literature" via annotations.  Annotations are exempt from publisher's
usage restrictions, which means that anyone with access to a document
can submit it to an annotation server, layer annotations upon the
document, and publicize these annotations.

Third, by integrating human feedback and meta-annotation of these
primary annotations, we can help provide algorithm authors with
"eyeballs" and corrections on their annotations.  This kind of
feedback will help drive better annotation algorithms.

Fourth, with tools to compare collections of annotations across large
bodies of papers, we will enable meta-analysis of annotation networks
and be able to build connections between overlapping but disparate
subfields of scientific literature.

A list of use cases
-------------------

(Expand on these.)

Wormbase & Textpresso integration - Wormbase has integrated a large
body of literature into its database, and we could help reverse the
Textpresso system to annotate the source literature with links into
the database.

Duplication, version, and plagiarism analysis - it would be
straightforward to identify cases where highly similar annotations
were placed on different document IDs, which could then be examined
for document equivalence, different versions, or plagiarized text.

Distributed commenting and aggregation of pre/post-publication peer
review of literature.  Basically, a way to take comments from multiple
locations and link them directly to the relevant text, pubmed records,
etc.

Back citation from future literature, including identification of
retracted citations, comments, and blog posts on the work and derived
works.

Place forward links to software, computational workflows, & replications of
published work on papers automatically.

What would we spend the money on?
---------------------------------

* hackathons & barnraisings
* developer
* ??

Architecture
------------

The basic architecture is::

  content -> engine + existing annotations -> new annotations

The Web server arch would be::

  content -> server running engine + retrieving existing annots -> new annots

The main question up front is whether we go for a single server with multiple
annotation engines (probably good for a prototype) or rather plan around
multiple servers each running one or a few engines.

Leftover text
-------------

We believe that this functionality can be usefully augmented by
building server-side functionality that will enable anyone with access
to a document to annotate the document using their own process and
information. This expands the information available for annotation
beyond what is available in the browser and the document itself.  For
example, someone with access to large bodies of papers could annotate
with the results of data mining applied to the paper; or, users with
institutional access to closed-access publications could submit those
publications to a ContentMine server for open annotation; or,
biological databases could use their special knowledge of identifiers
to provide annotations based on a compute-intensive analysis; or,
publishers and institutions could provide a "first look" of annotation
for their own document collections; or, reviewers could privately
annotate papers they are reviewing with an automated system to identify
relevant literature.

