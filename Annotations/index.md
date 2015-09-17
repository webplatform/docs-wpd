---
title: 'Annotations'
uri: 'WPD:Annotations'

---
This is a scratch space for adding annotations to WebPlatform.org and to W3C specifications.

## Background

We want to enable annotations on W3C specifications and on WebPlatform.org, as a way to provide feedback into specs and documentation.

The specific implementation we want to use will be based on the [Annotator project](http://okfnlabs.org/annotator/), as implemented and enhanced by [Hypothes.is](http://hypothes.is/), with an eye towards standardization informed by the [W3C Open Annotation Community Group](http://w3.org/community/openannotation/).

## Status

-   [Notes.WebPlatform.org](https://notes.webplatform.org/) (a.k.a. "annotator") is deployed and running
-   Accounts server who’s taking care of authentication and OAuth authorizations is deployed and running
-   Annotations is enabled on those W3C specs:
    -   [Annotation Model](http://www.w3.org/TR/annotation-model/)

### Email Notifications

-   E-mail notifications of annotations sent to W3C archive mailing list would work only when annotator is loaded on "w3.org" and "specs.webplatform.org".

### Current issues

Refer to [webplatform/annotation-service issue tracker](https://github.com/webplatform/annotation-service/issues)

## Requirements to make annotations on specs

-   Credentials for identity on **accounts.webplatform.org** username and password
-   To get Mailing list archive
    -   Documents must be hosted on "w3.org" or "specs.webplatform.org'"
    -   Must contain

``` html
<a href="mailto:public-listname@w3.org" rel="reply-to">list name label</a>
```

-   To make annotations on more than one URI but for the same spec, use canonical *link* tag in *head* of Document, e.g.

``` html
<link rel="canonical" href="http://www.w3.org/TR/annotation-model/">
```

## Interface

-   Toggle annotation functionality on or off
    -   Can annotations be enabled without an extension, or must the user install an extension? Is there a script that could be hosted to do the same thing?
-   Show annotations on demand
-   Optional: Add special "classes" of annotation, such as tests results, that display differently in the spec than simple text annotations (perhaps as icons for browser support)
    -   **"editorial":** grammar change, typo, clarification
    -   **"normative":** change to technical requirements of spec
    -   **"request":** suggestion for new feature
    -   **"testable":** marks section of spec as a testable assertion that needs one or more tests
-   Provide separate document view of annotations outside sidebar context (e.g. a page that lists all annotations for a site, on a per-page, per-tag basis)
-   Provide status states, like:
    -   **"new"**
    -   **"accepted"**
    -   **"assigned"**
    -   **"resolved"**
    -   **"rejected"**
    -   might reuse existing hashtag functionality, with special behavior for certain states
-   Provide different "annotation modes" specific to different tasks, filtering/hiding (based on tags) annotations for the other modes:
    -   **"spec review"**
    -   **"testable assertion"**
    -   **"implementation and test status"**
    -   **"documentation note or link"**

## Links

-   [Scenarios](/WPD:Annotations/Scenarios)
-   [Workflows](/WPD:Annotations/Workflows)
