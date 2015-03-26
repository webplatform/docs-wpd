{{:WPD:Infrastructure/architecture}}
= Maintaining Varnish/Fastly configuration =

The following summarizes how to manage our Varnish caching service served by our friends at [https://fastly.com Fastly]. Note that the documentation describes how Varnish works but also how to manage Fastly very own Varnish cluster so we don’t have to.

This document is specific on how to maintain Varnish configuration at Fastly. Notes that describes the specifics of things we should keep in mind when configuring the cache should be moved to [[WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish|Things to consider when we expose service via Fastly and Varnish]]

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

'''Reminder''' more notes about specifics for each web application we deployed are noted in  [[WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish|'''Things to consider when we expose service via Fastly and Varnish''']]

== Accessing VCL configuration from Fastly ==
[[File:20131121-Fastly-vcl-buttons.png]]
To access/overwrite the file in Fastly, go to:
* [https://app.fastly.com/ Fastly pannel], login
* Select targeted site (e.g. ''docs.webplatform.org'')
* Configure tab on top, Configure button
* VCL on the left

==== Wizard to add a backend host ====

While describing how to debug an issue we had with Semantic MediaWiki, I described how to change which public IPs would be proxyed by Fastly.

The screenshot below is described in [[WPD:Infrastructure/procedures/Rebuilding_Semantic_Media_Wiki_when_job_queue_is_going_out_of_control]]

[[File:fastly-docs-service-hosts-screenshot.png]]

=== Current Fastly configuration ===
Make the content of snippet as a file and upload it to the Fastly control pannel.

Configuration files are stored on [https://github.com/webplatform/varnish-configs Github, in '''webplatform/varnish-configs''' project], the VCL file name should match the subdomain and also the service bane in Fastly dashboard.

== Reference ==

* [https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL- Fastly: How to mix and match Fastly VCL with custom VCL (Varnish configuration file)]
* [https://github.com/webplatform/varnish-configs '''WebPlatform''' varnish-configs GitHub repository]
* See also more notes on the topic at [[WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish|Things to consider when we expose service via Fastly and Varnish]]