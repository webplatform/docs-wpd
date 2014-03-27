== Homepage project ==
=== Summary ===
This document describes the status and points to other related documentation for the home page and various static content that aren't managed by a CMS. 

The code is available on [https://github.com/webplatform/www.webplatform.org github.com/webplatform.org/www.webplatform.org], you can also report issues in [https://github.com/webplatform/www.webplatform.org/issues/new?title=Describe%20issue%20found%20&labels=bug&assignee=renoirb&body=URL:%20Insert%20address%20where%20you%20found%20the%20problem the repository issue tracker].


=== Scope ===
Static content are pages that we do not want to allow edition without audit such as: The homepage, error documents, the stewards pages. Since the pages are't going to change frequently and they are served from a cookie-less domain (''www.webplatform.org'') and facilitate the caching configuration for files and pages that are not changed frequently.

=== Objectives ===
# Workspace where a contributor can fork and improve CSS and JavaScript assets
# Serve from one place all CSS and JavaScript, already minified (currently MediaWiki's minifier; create load for no real benefit)
# Ensure uniformity in pages without relying on server side language
# Provide a workspace where we can focus on HTML/CSS/JavaScript without backend code involved.

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
[[User:renoirb]] has personally tried a few static site generators and found that [http://docpad.org/ DocPad] was the right choice. Among the technologies tried we had: Assemble, Octopress, Jekyll,  and Ghost.  What made the choice clear was that it took less than one hour to be able to do basic things described in the [[#Requirements]].  

Besides the fact that DocPad was  uses CoffeeScript, we are not forced to use it in our own code.