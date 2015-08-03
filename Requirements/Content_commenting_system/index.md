---
title: WPD:Requirements/Content commenting system
---
<h1><span class="mw-headline" id="Content_commenting_system">Content commenting system</span></h1>
<h2><span class="mw-headline" id="Overview">Overview</span></h2>
<p>We want an extension to allow users on our wiki to comment on particular sections of wiki page, in an way that is unobtrusive for readers.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Environment">Environment</span></h2>
<p>Semantic MediaWiki installation on dedicated servers, and several other extensions (including Semantic Forms, and Social Profile).
</p>
<h2><span class="mw-headline" id="Specifications">Specifications</span></h2>
<p>The basic idea we want to reproduce (with improvements) is the Django Book commenting system <a rel="nofollow" class="external autonumber" href="http://djangobook.com/en/2.0/chapter02/">[1]</a>; click on the bubbles on the side, and look at the "help" tab for more details.
</p><p>My idea for implementation is that we would have some forum software installed (either a MediaWiki extension like WikiForum <a class="external autonumber" href="http://www.mediawiki.org/wiki/Extension:WikiForum">[2]</a> or AWC's Forum <a class="external autonumber" href="http://www.mediawiki.org/wiki/Extension:AWC%27s_Forum">[3]</a>, or an external forum like phpBB). Each page would be represented by a "forum topic" and each section with a separate thread in that topic; when a user creates a new comment, it creates a new thread (and a new topic, if no comments exist for that page). Each thread would be attached to a particular section by the ID of that section.
</p><p>This forum interface would be rendered as the content of a "popup dialog" iframe, on the same page; from the user's perspective, they are still on the same page. The forum should be greatly simplified for this use.
</p><p>However, this is just my idea of how this could be executed; another approach might be to use each page's MediaWiki Discussion Page as the comment repository... but it should still be threaded.
</p><p><br />
Requirements:
</p>
<ul><li> Must allow comments on a per-section basis (using section ids)
<ul><li> Must show "bubble" for each section that has comments</li>
<li> Bubble must show number of comments for that section
<ul><li> Comment dialog area (probably an iframe, not a separate window) should pop up when bubble is clicked</li>
<li> Comment dialog must be dismissable (e.g. can be closed)</li></ul></li>
<li> Comments must be threaded (so people can comment on comments)</li>
<li> All comments on a page should be visible through another view</li>
<li> Comments must be "resolvable" (e.g. marked as solved and hidden when the comment has been addressed)</li>
<li> Comments must be retained even if section has been removed (but doesn't need to necessarily be available via a bubble)</li></ul></li>
<li> New comments can be made in an intuitive way (e.g. by clicking on the side of a section, like in DjangoBook)
<ul><li> Only logged-in users can comment, but anyone can view comments</li></ul></li>
<li> Readers should be able to turn off comment bubbles</li>
<li> Comment dialog area should be draggable
<ul><li> Default position of comments should be off to one side or the other, so it doesn't obscure the body text</li></ul></li>
<li> Comment dialog are must be stylable with skin's CSS.</li>
<li> Prefer if comments are not be stored inline in the wiki page</li></ul>
<p>Nice-to-have:
</p>
<ul><li> Ability to select specific passages (words or sentences) that are copied into comments, or highlighted in some way.</li>
<li> Ability to mod comments up or down</li>
<li> Ability to add certain "flags" (categories, tags, or templates) to the comment or to the page itself (e.g. if I'm commenting that a particular section contains factual errors, in addition to making the comment, I might like to tag my comment as "factual error", and have that insert a template ("flag") into the page</li>
<li> Comments might be "reattached" to a different section if content is reorganized... but this seems hard to do, unless it's just subsections; maybe all orphaned comments should be raised to the page level, and can be reattached to another section manually?</li>
<li> An API to read and write comments on a page and section</li>
<li> Comment dialog would ideally be resizable</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Credits_and_License">Credits and License</span></h2>
<p>We would want to release the extension as open source (preferably MIT license), with our name as sponsor, and your name as developer (if you want to be credited).
</p><p>We don't mind if your extension forks another extension, or relies on another (open source) extension; we just care that it works, and that it's done as soon as possible.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:7712-0!*!*!!*!*!*!esi=1 and timestamp 20150731183737 and revision id 50227
 -->
