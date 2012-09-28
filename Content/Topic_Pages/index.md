We have a number of landing pages implied by the [[WPD:Architecture]]. Most of them are captured in this migration tracking spreadsheet: https://docs.google.com/a/chromium.org/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c#gid=34

This page documents how to go about creating them.

The primary goal of these landing pages is to make sure that users (and search engines!) know about all of the content we have hidden within the site. The secondary goal is to explain the concepts that unite them.

There are a few types of pages:

==Manually generated==
Some pages are so specialized (and so little work to generate, and so unlikely to change) that it just makes sense for us to list them by hand. The main page is a good example--it needs to point to the major topic areas but those are few in number and change rarely.

The disadvantage is that if we generate them by hand they can get stale easily, so don't fall back to this unless you have to.

==Simple Sub-Directory==
If all you need to do is list all of the sub-directories, MediaWiki has some built in features.

The following snippet will print out all descendants of the given URL:
<pre>
{{Special:PrefixIndex/WPD:Example_Pages/}}
</pre>
Where "/WPD:Example_Pages/" is the prefix of the URL to list the descendants of. However, this has a '''crucial limitation''': it automatically prints out all ''descendants'', where often all you want is the ''children''.

We installed the SubPageList extension to help with this.

The code snippet you'll probably use most often is this: 
<pre>
{{#subpages: | kidsonly=Yes}}
</pre>

The first parameter is omitted because it's the URL to list sub-pages of, and if you omit it it defaults to the current page.

You can read more at http://www.mediawiki.org/wiki/Extension:SubPageList

==Query-generated==