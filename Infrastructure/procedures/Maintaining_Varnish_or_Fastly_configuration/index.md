{{:WPD:Infrastructure/architecture}}
= Maintaining Varnish/Fastly configuration =

The following summarizes how to manage our Varnish caching service served by our friends at [https://fastly.com Fastly]. Note that the documentation describes how Varnish works but also how to manage Fastly very own Varnish cluster so we don’t have to.

== Abastract ==

If your system uses cookies, which is most of the time the case, Varnish does not caches. The configuration MUST to be adjusted to each site specifics. Details such as a web application sending HTTP headers such as Cache-Control, Set-Cookie, Cookie can still prevent caching to happen.

This page is about keeping notes on current Varnish configuration files and notes to help maintaining an appropriate caching strategy. 

== NOTES ==

=== Varnish version and limitations ===
An important detail to remember is that Fastly is using Varnish 2.1.4, their configuration specifics do not support either pipe, ban, nor purging with ACL. 

Also, the way to provide CDN service is with what they call "Shield", it is basically a layer of application that stores a local copy of what is grabbed by a service backend server. Provided that the backend server do not explicitly prevent caching, or that the VCL has appropriate adjustments, Fastly will send files from the Shield before hitting again the backend servers.

VCL is the Varnish Configuration language file, throughout the panel, we can see two VCL buttons, the one beside the service name and revision is to download the generated VCL, whereas we can also provide our own VCL that must have keywords so the panel adds content to it.

A recommended way to work is to follow '''[https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL-  How do I mix and match Fastly VCL with custom VCL]'''

=== Details to consider ===

==== MediaWiki ====
Here are the specifics for MediaWiki
* Note that most of the cookies starts with the ''$wgDBname'' string from the ''Settings*.php'' file. In the list below, its value is 'wpwiki'.
* Delete all cookies, except: wpwikiUserID, wpwiki_session, wpwikiUserName, Token, LoggedOut, dismissSiteNotice
* Only place to set cookies are when UserLogin, UserLogout

== Accessing VCL configuration from Fastly ==
[[File:20131121-Fastly-vcl-buttons.png]]
To access/overwrite the file in Fastly, go to:
* [https://app.fastly.com/ Fastly pannel], login
* Select targeted site (e.g. ''docs.webplatform.org'')
* Configure tab on top, Configure button
* VCL on the left


=== Current Fastly configuration ===
Make the content of snippet as a file and upload it to the Fastly control pannel.

Configuration files are stored on [https://github.com/webplatform/varnish-configs Github, in '''webplatform/varnish-configs''' project], the VCL file name should match the subdomain and also the service bane in Fastly dashboard.

== Links ==
=== MediaWiki ===
* [http://www.mediawiki.org/wiki/Manual:Varnish_caching MediaWiki Varnish Caching]
* [http://labs.creativecommons.org/2011/03/18/caching-mediawiki-with-varnish/ Caching mediawiki with varnish]
* [https://www.varnish-cache.org/lists/pipermail/varnish-misc/2012-January/021574.html Default VCL for MediaWiki]


=== Fastly specific ===
* [https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL- Fastly: How to mix and match Fastly VCL with custom VCL (Varnish configuration file)]
* [http://kly.no/posts/2010_01_08__Hitpass_objects_and_Varnish__.rst Varnish caching, definition of HIT, PASS and other caching lingo]
* [http://docs.fastly.com/guides/21847086 Fastly: Caching tutorials]
** [http://docs.fastly.com/guides/21835572/21744408 Fastly: Removing headers from backend response]
** [http://docs.fastly.com/guides/21835572/23999817 Fastly: Adding and modifying headers]
** [http://docs.fastly.com/guides/21847086/22257776 How to serve stale content in case of origin becoming unavailable]
* [http://docs.fastly.com/guides/21847086/26628787 Fastly tutorial: Cache control]

=== Varnish in general ===
* [http://kly.no/varnish/regex.txt Regular expression Cheat sheet]
* [https://www.varnish-cache.org/docs/2.1/genindex.html Varnish documentation]
** [https://www.varnish-cache.org/docs/2.1/tutorial/vcl.html Varnish configuration language]
** [https://www.varnish-cache.org/docs/2.1/tutorial/cookies.html Varnish tutorial cookies]
* [https://www.varnish-software.com/static/book/Tuning.html?highlight=timeout Varnish book about tuning]

=== ESI ===
* [https://www.varnish-cache.org/trac/wiki/ESIfeatures Varnish ESI features]
* [https://www.varnish-cache.org/docs/2.1/tutorial/esi.html Varnish 2.1 ESI doc]