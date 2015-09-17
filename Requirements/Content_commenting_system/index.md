---
title: 'Content commenting system'
uri: 'WPD:Requirements/Content commenting system'

---
## Overview

We want an extension to allow users on our wiki to comment on particular sections of wiki page, in an way that is unobtrusive for readers.

## Environment

Semantic MediaWiki installation on dedicated servers, and several other extensions (including Semantic Forms, and Social Profile).

## Specifications

The basic idea we want to reproduce (with improvements) is the Django Book commenting system [[1]](http://djangobook.com/en/2.0/chapter02/); click on the bubbles on the side, and look at the "help" tab for more details.

My idea for implementation is that we would have some forum software installed (either a MediaWiki extension like WikiForum [[2]](http://www.mediawiki.org/wiki/Extension:WikiForum) or AWC's Forum [[3]](http://www.mediawiki.org/wiki/Extension:AWC%27s_Forum), or an external forum like phpBB). Each page would be represented by a "forum topic" and each section with a separate thread in that topic; when a user creates a new comment, it creates a new thread (and a new topic, if no comments exist for that page). Each thread would be attached to a particular section by the ID of that section.

This forum interface would be rendered as the content of a "popup dialog" iframe, on the same page; from the user's perspective, they are still on the same page. The forum should be greatly simplified for this use.

However, this is just my idea of how this could be executed; another approach might be to use each page's MediaWiki Discussion Page as the comment repository... but it should still be threaded.

 Requirements:

-   Must allow comments on a per-section basis (using section ids)
    -   Must show "bubble" for each section that has comments
    -   Bubble must show number of comments for that section
        -   Comment dialog area (probably an iframe, not a separate window) should pop up when bubble is clicked
        -   Comment dialog must be dismissable (e.g. can be closed)
    -   Comments must be threaded (so people can comment on comments)
    -   All comments on a page should be visible through another view
    -   Comments must be "resolvable" (e.g. marked as solved and hidden when the comment has been addressed)
    -   Comments must be retained even if section has been removed (but doesn't need to necessarily be available via a bubble)
-   New comments can be made in an intuitive way (e.g. by clicking on the side of a section, like in DjangoBook)
    -   Only logged-in users can comment, but anyone can view comments
-   Readers should be able to turn off comment bubbles
-   Comment dialog area should be draggable
    -   Default position of comments should be off to one side or the other, so it doesn't obscure the body text
-   Comment dialog are must be stylable with skin's CSS.
-   Prefer if comments are not be stored inline in the wiki page

Nice-to-have:

-   Ability to select specific passages (words or sentences) that are copied into comments, or highlighted in some way.
-   Ability to mod comments up or down
-   Ability to add certain "flags" (categories, tags, or templates) to the comment or to the page itself (e.g. if I'm commenting that a particular section contains factual errors, in addition to making the comment, I might like to tag my comment as "factual error", and have that insert a template ("flag") into the page
-   Comments might be "reattached" to a different section if content is reorganized... but this seems hard to do, unless it's just subsections; maybe all orphaned comments should be raised to the page level, and can be reattached to another section manually?
-   An API to read and write comments on a page and section
-   Comment dialog would ideally be resizable

## Credits and License

We would want to release the extension as open source (preferably MIT license), with our name as sponsor, and your name as developer (if you want to be credited).

We don't mind if your extension forks another extension, or relies on another (open source) extension; we just care that it works, and that it's done as soon as possible.
