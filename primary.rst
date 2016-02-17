Annotation as a service: helping build a global knowledge layer with annotation of the dark literature.
=======================================================================================================

Codename: Aesir. (Suggestions welcome. ;)

We propose to build server-side functionality to enable anyone to
consume text and add annotations to it, using the hypothesis
annotation system.

Hypothesis is an annotation overlay that allows annotations to be
associated with text. Each annotation consists of a document ID, a
document anchor, some free text, and tags; annotations can be either
public or belong to private groups.  The hypothesis service currently
offers an overlay display where these annotations are placed on HTML
or PDF views of documents. Annotations can be placed manually on
documents via a Google Chrome plugin or a JavaScript code snippet;
they are stored in the hypothesis central database and can be
retrieved on demand for any specified document ID.

We believe that this functionality can be usefully augmented by
building server-side functionality that will enable anyone with access
to a document to annotate the document using their own process and
information. This expands the information availabe for annotation
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

Three use cases this would enable
---------------------------------

1. Aeneas is reading a paper from 2004 on a closed-access site, and is
   interested in knowing who has cited the paper, linking to back
   references and identifying which have been retracted, and seeing what
   databases have used the information from the paper.  Because the
   paper is not accessible to any automated annotation services, none of
   this information can be posted on the paper. Aeneas submits the paper
   to the Aesir annotation server with a click, which annotates it and
   "paints" the paper with annotations.
   
2. Tina has access to an otherwise inaccessible paper, and wants to
   apply `ContentMine <http://contentmine.org/>`__ to it.  She cannot
   give ContentMine direct access to it. Tina submits the paper
   to an Aesir server running ContentMine, which annotates the paper.

3. James is reviewing a paper, and wants to mark it up with blog
   commentary and public reviews.  Unfortunately, the paper is a
   revision of a posted preprint and so its hypothesis ID has changed
   and no annotations are associated with it; James submits the paper
   to a service that identifies it as a duplicate of a previously
   annotated paper and transfers the annotations over to it where possible.

Deliverables
------------

The first line of deliverables would be a full server (implemented in
Python) for adding annotations to documents, together with JavaScript
bookmarklets to enable submission of documents to such servers from
within any modern Web browser.  The server code would contain an open
source implementation of the parsing and annotation-marking logic used
in hypothesis, providing a framework that would readily enable
developers to consume text and annotate it according to their own
logic.  We would provide a full demo server implementation using a
public open source code base (e.g. ContentMine).

On top of these deliverables we plan a variety of services, depending
on where we see opportunities:

* large-scale annotation search and comparison, so that documents can
  be grouped and analyzed based on their annotations and larger
  networks of annotations;
   
* enable human feedback on and editing of automated annotations, so that viewers can annotate annotations and identify misannotations;
  
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

Outcomes:

first and foremost, we envision this as providing entree to the "dark
literature" via annotations.  Annotations are exempt from publisher's
usage restrictions, which means that anyone with access to a document
can submit it to an annotation server and layer annotations upon the
document.

second, we believe we can enable an ecosystem of annotation
algorithms, some general (e.g. linguistic analysis of document
structure) and some field-specific (e.g. automated extraction and
annotation of drug-drug interactions across document collections).

third, by integrating human feedback and meta-annotation of these
primary annotations, we can help provide algorithm authors with
"eyeballs" and corrections on their annotations.  This kind of
feedback will help drive better annotation algorithms.

fourth, with tools to compare collections of annotations across large
bodies of papers, we will enable meta-analysis of annotation networks
and be able to build connections between overlapping but disparate
subfields of scientific literature.

Specific use cases; expand on some:

Wormbase & Textpresso integration - Wormbase has integrated a large
body of literature into its database, and we could help reverse the
Textpresso system to annotate the source literature with links into
the database.

Duplication, version, and plagiarism analysis - it would be
straightforward to identify cases where highly similar annotations
were placed on different document IDs, which could then be examined
for document equivalence, different versions, or plagiarized text.

Annotation and mark up of scientific teaching materials. Not sure what
I was thinking here, but probably something to do with Software and Data
Carpentry, and literature.

Distributed commenting and aggregation of pre/post-publication peer
review of literature.  Basically, a way to take comments from multiple
locations and link them directly to the relevant text, pubmed records,
etc.

Back citation from future literature, including identification of
retracted citations, comments, and blog posts on the work and derived
works.

Forward links to computational workflows and replications of published
work.
