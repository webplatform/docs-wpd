= Summary =
A MediaWiki extension to read data from a JSON object into human readable HTML tables showing browser feature compatibility.

This page describes the use of the data we publish, 


== Logistics ==
* '''Project page''':  See  [[WPD:Projects/CompaTables]]
* '''How we added to our content''': [[WPD:Projects/CompaTables/Adding_to_our_content]]
* '''Implementation details''':  See  [[WPD:Infrastructure/Components/CompaTables]]
* '''Add data''': Make a [https://github.com/webplatform/compatibility-data ''pull requests'' in '''compatibility-data''' repo]
* '''Found bug in visualisation''': Create an issue in [https://github.com/webplatform/mediawiki/issues/new?title=Table%20display%20issue%20in%20URL%20&labels=CompaTables&assignee=renoirb&body=URL:%20Insert%20address%20where%20you%20found%20the%20problem the CompaTables Extension project issue tracker]

== FAQ ==

=== How do you get the compatibility tables on your docs pages? ===

We created a [[WPD:Infrastructure/Components/WebPlatformDocsExtensionBundle|MediaWiki extension "WebPlatformDocs Extension bundle"]] that takes care of generating the HTML views you see on our documentation pages. This extension reads the data from flat-file JSON file.

Each documentation page that should require a compatibility table have, in some way, an inclusion of the [http://docs.webplatform.org/wiki/Template:Compatibility Template:Compatibility "template"]. If you want to see how we set the inclusion in place, head over to  [[WPD:Projects/CompaTables/Adding_to_our_content]].

=== Can I get and use the data? ===

Sure you can!  Our compatibility table is based on a raw JSON file and you can use it too.  We serve it from [http://docs.webplatform.org/compat/data.json '''docs.webplatform.org/compat/data.json'''], and also serve an idempotent [http://docs.webplatform.org/compat/data.json "''human friendly''" ('''data-human.json''') version with indentation]. 

If you are command line inclined, you can also make queries to it using ''[https://github.com/ddopson/underscore-cli underscore-cli]''. The page [[WPD:Projects/CompaTables/Reading_the_data.json_file]] explains how to do.


=== Can I improve the data? ===

Sure!  At this time, we published our raw compatibility data as [https://github.com/webplatform/compatibility-data '''webplatform/compatibility-data''' on GitHub]. The manual edition is a temporary process until we improve it.