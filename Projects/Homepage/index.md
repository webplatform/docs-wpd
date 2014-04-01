== Homepage project ==
=== Summary ===
This document describes the status and points to other related documentation for the [http://www.webplatform.org www.webplatform.org "landing  page"] and various static content that aren't and should not be managed by a CMS. 

The code is available on [https://github.com/webplatform/www.webplatform.org github.com/webplatform.org/www.webplatform.org], you can contribute by forking and submitting a pull-request,  report issues in [https://github.com/webplatform/www.webplatform.org/issues/new?title=Describe%20issue%20found%20&labels=bug&assignee=renoirb&body=URL:%20Insert%20address%20where%20you%20found%20the%20problem the repository issue tracker].


=== Scope ===
Static content are pages that we do not want to allow edition without audit such as: The landing page,  the stewards section, the logo, and error pages. Since those pages are't going to change frequently we could use serve plain static files directly, and when we need to change content, leverage a static site generator to create the documents but prevent us copy-pasting code through many files.

Also, in order to improve the load time our our page, we could set in place workflows that helps us organize our CSS/JavaScript files and allow us to serve them with appropriate caching headers and reduced file-size (i.e. minification). Since the content at ''www.webplatform.org'' is mostly static, doesn't have application that requires cookies it will help us increase our HTTP cache HIT rate for both static pages and CSS/JavaScript files.


=== Objectives ===
# Workspace where a contributor can fork and improve CSS/JavaScript assets
# Serve from one place all CSS/JavaScript, already minified (currently using MediaWiki's minifier; create load for no tangible benefit)
# Ensure uniformity in pages without relying on server side language
# Provide a workspace where we can focus on HTML/CSS/JavaScript without backend code involved


=== Requirements ===
==== Functional ====
# Leverage tools to generate, concatenate, validate, minify assets before deploying; serving only static files to the live site.
# Support pages nesting in directories, for example: ''stewards/microsoft''
# Support multiple tools (e.g. Process Markdown to HTML, Process templating engine, etc)

==== Non functional ====
# Workspace has to allow contributor to use without a too steep learning-curve
# Tools to use the language of the Web Platform (e.g. JavaScript)
# Serve as a reference to illustrate current Frontend development best-practices
# Have as less as possible technology requirements (i.e. if we can rely only on JavaScript+Node, the better)

=== Choice ===
[[User:renoirb]] has personally tried a few static site generators and found that [http://docpad.org/ DocPad] was the most sensible choice. What made the choice clear was that it took less than one hour to be able to do basic things such as sub pages, and other things described in the [[#Requirements]] sections.  Among the projects [[User:renoirb]] tried were: Assemble, Octopress, Jekyll,  and Ghost.

Besides the fact that DocPad was  uses CoffeeScript, we are not forced to use it in our own code.

== See also ==
* [https://gist.github.com/balupton/5519403  Use DocPad to pull and render content from a GitHub repository]