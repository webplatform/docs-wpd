= Summary =
A MediaWiki extension to read data from a JSON object into human readable HTML tables showing browser feature compatibility.

This component is part of [[WPD:Infrastructure/Components/WebPlatformDocsExtensionBundle|WebPlatformDocs MediaWiki extension bundle]], you can read how we are including the template in [http://docs.webplatform.org/wiki/Template:Compatibility Template:Compatibility] and which other templates are using it in [[WPD:Projects/CompaTables/Adding_to_our_content]].

We provide both the [http://docs.webplatform.org/compat/data.json '''docs.webplatform.org/compat/data.json''' raw data as a flat file], and a [http://docs.webplatform.org/compat/data.json "''human friendly''" ('''data-human.json''') version] counterpart that we use to author and is available for contribution as [https://github.com/webplatform/compatibility-data '''webplatform/compatibility-data''' on GitHub]. The manual edition is a temporary process until we improve it.