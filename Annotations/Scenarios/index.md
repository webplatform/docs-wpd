---
title: Scenarios
uri: 'WPD:Annotations/Scenarios'

---
## Reviewing Specifications

A reader wishes to read and provide feedback on a W3C specification.

See [Workflows](/WPD:Annotations/Workflows).

## Identifying Documentation Points

1.  A reader wishes to identify basic features of a spec that need to be documented. For example, a reader could walk through a CSS spec and annotated each of the CSS properties. Note that the reader does not have to understand the feature or have to document it themselves; that is a separate task.
2.  A reader wishes to highlight a specific passage in a spec as being important for a documentation site to provide clear developer/designer guidance on. For example, a reader notices a tricky, unexpected detail in the specification for the CSS border-radius property that they think needs a call-out in the documentation. Note that the reader may be an expert, or may be a newbie who is requesting a specific explanation.

### Issues

-   Annotations should be able to be marked as relevant for documentation
    -   Annotation tool could provide a UI that inserts the appropriate tag into that annotation
-   Annotations on a spec should be reflected not only in sidebar of spec, but in a requirements document for contributors to documentation site (e.g. WebPlatform.org)
    -   Annotation server could provide multiple views of document, including one that adds annotation to appropriate page on documentation site (e.g. If a reader highlights a tricky part of CSS border-radius that needs explanation, annotation tool could show that annotation in the spec, but also on docs.webplatform.org/wiki/css/properties/border-radius page, and also on a generated page that list all annotations for CSS issues.

## Indicating Documentation Points

A Working Group wishes to inform the reader where to find developer/designer documentation for any given feature in a specification.

## Issues

-   WG wishes to automate this task
    -   Annotation tool / server could provide an API for bots to add or update annotations based on a known, consistent scheme for documenting features (e.g. a regular site hierarchy or metadata)
    -   Documentation contributors could ensure that relevant specs are listed in page for documented feature, making it easier for a bot to automate this task

## Notification of Change of Specification

A documentation project wishes to keep their documentation in sync with changes made to a related specification, and to indicate that stability and status to their readers.

## Issues

-   Project wishes to automate this task
    -   Annotation tool / server could provide an API for bots to add or update annotations based on a known, consistent scheme for documenting features (e.g. a regular site hierarchy or metadata)
    -   Documentation contributors could ensure that relevant specs are listed in page for documented feature, making it easier for a bot to automate this task
-   Project wishes to be notified of changes to the spec
    -   A bot could monitor publications, run a diff on specific sections of the versions of a spec, and add annotations to the appropriate page on the documentation site indicating a change

## Identifying Testable Assertions

A reader wishes to manually walk through the spec and identify selections for suitability (or need) for testing.

### Issues

-   User may wish to select multiple non-contiguous passages, on the same or different pages in the same document, for combinatorial testing
    -   UI could provide a way to add selection passages to same annotation

## Indicating Status of Tests or Implementations

A Working Group wishes to inform the reader which parts of the spec are at different levels of stability, in terms of number of tests or known implementations, and wishes to provide links to tests and implementation reports.

### Issues

-   These annotations should be indicated in a different way than normal text annotations
    -   Annotation tool could insert icons on a per-section level indicating status
    -   Annotation tool could style feature / section name differently based on relative stability, or give stability marker
-   WG wishes to automate this task
    -   Annotation tool / server could provide an API for bots to add or update annotations

## Keeping Private Notes on Specifications

A reader, or set of reader, wish to highlight and annotate parts of the spec for personal/internal review, before commenting on them publicly. For example, a company may wish to discuss the IP considerations of a spec, comparing to their IP portfolio, or known IP from others, as part of a risk assessment.

### Issues

-   User doesn't wish to share annotations with others (yet or ever)
    -   Annotation tool could allow user to store (non-sensitive) on normal annotation server with view permissions set to self or set of friends
    -   Important that annotations are not simply hidden by CSS, but rather not downloaded for unauthorized users at all
-   User may not wish sensitive annotations to be stored on a external site
    -   Annotation tool could be configured to store annotations on user's own annotation server
    -   User could use their own annotation tool and server

## Unanchored Annotation

A reader wishes to leave an annotation or comment about the site as a whole, not a particular page. For example, a reader may wish to add a feature request for the site, or comment on the quality of the site as a whole.

### Issues

-   Annotations should be anchorable to the site without a page referent
    -

-   Unanchored annotations should be allowed to be added while on any site of the page without anchoring to that page
    -

-   Unanchored annotations should not accumulate on the site landing page or index page, because they will clutter that page
    -

