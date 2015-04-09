{{Page_Title}}
{{Flags
|Checked_Out=No
}}
{{Summary_Section|This page contains some quick guides to performing small maintenance tasks, which we thought were too small to put on their own separate pages.}}
{{Basic Page}}
==Migrating a non-form-based page to use the proper form==

On Webplatform.org, all standard pages should be based on the correct form, but you may come across a page that has been created without using the correct section of [[WPD:New_Page]]. If you do come across such a page, you should follow these simple steps to fix it.

# Save the content of the non-form-based page somewhere handy on your local machine
# Find a page with the same page type that you want to convert the non-form-based page to. This should be pretty simple - you can find the URL schema from [[WPD:New_Page]] and then use that to browse to an appropriate page. If you find this ineffective, send a mail around the public mailing list asking for assistance, and someone else will be glad to assist you.
# Select "Edit source" on this page, then copy the entire contents over to the content of the non-form-based page.
# Save the page — this should convert it to being a form-based page.
# Select "Edit" on this page, and you should now be able to use the form to edit the content on the previously-non-form-based page!
# Copy your original content into the appropriate form fields.

== Get statistics ==

* [[Special:Statistics|Statistics Special page]] or its command-line equivalent [https://www.mediawiki.org/wiki/Manual:ShowSiteStats.php ''showSiteStats'' maintenance script], e.g.  <code>php mediawiki/maintenance/showSiteStats.php</code>
** Refresh site stats with [https://www.mediawiki.org/wiki/Manual:InitSiteStats.php ''InitSiteStats.php''], e.g.  <code>php mediawiki/maintenance/initSiteStats.php</code>

=== Other stats tools ===

==== [https://meta.wikimedia.org/wiki/StatMediaWiki StatMediaWiki] ==== 

'''Outcome:''' Couldn’t make something work in a reasonable time.

TL;DR. Its a Python project can read from a database snapshot, crunch some data, and generate reports. Unfortunately, it has next to no docs, although I could get something at [http://edutechwiki.unige.ch/en/StatMediaWiki in this wiki]. 

Unfortunately it seems the Python code is making database queries to MediaWiki database tables changed since the time ''StatMediaWiki'' was made and wasn’t completing execution. 

See also the [https://meta.wikimedia.org/wiki/Talk:StatMediaWiki StatMediaWiki Talk page]

==== [https://www.mediawiki.org/wiki/Extension:Usage_Statistics Usage Statistics Extension] ====

'''Outcome:''' Couldn’t make it work due to incompatibility caused by some calls that were using deprecated methods.

=== Also ===

* https://meta.wikimedia.org/wiki/WikiXRay
* https://www.mediawiki.org/wiki/Analytics/Wikistats https://stats.wikimedia.org/
* http://reportcard.wmflabs.org/ https://github.com/wikimedia/limn
{{Notes_Section}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
}}