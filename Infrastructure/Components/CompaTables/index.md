= Summary =
A MediaWiki extension to read data from a JSON object into human readable HTML tables showing browser feature compatibility.

This component is part of [[WPD:Infrastructure/Components/WebPlatformDocsExtensionBundle|WebPlatformDocs MediaWiki extension bundle]], you can read how we are including the template in [http://docs.webplatform.org/wiki/Template:Compatibility Template:Compatibility] and which other templates are using it in [[WPD:Projects/CompaTables/Adding_to_our_content]].

== Can I get and use the data? ==

Sure you can!  Our compatibility table is based on a raw JSON file and you can use it too.  We serve it from [http://docs.webplatform.org/compat/data.json '''docs.webplatform.org/compat/data.json'''], and also serve an idempotent [http://docs.webplatform.org/compat/data.json "''human friendly''" ('''data-human.json''') version with indentation]. 

If you are command line inclined, you can also make queries to it using ''[https://github.com/ddopson/underscore-cli underscore-cli]''. The page [[WPD:Projects/CompaTables/Reading_the_data.json_file]] explains how to do.


== Can I improve the data? ==

Sure!  At this time, we published our raw compatibility data as [https://github.com/webplatform/compatibility-data '''webplatform/compatibility-data''' on GitHub]. The manual edition is a temporary process until we improve it.