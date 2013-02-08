One planned feature of Web Platform Docs is a live code viewer and pastebin. 

The webapp we are using for this is [http://dabblet.com/ Dabblet], which will be integrated into the site.

==Features==

==Integration==
Because integration has many aspects, we will roll out full support for this feature in several steps.

===Roadmap===
====Phase 1: Static Live Code Viewer====

'''Status:''' ''in progress''

====Phase 2: Open Examples from Wiki====

'''Status:''' ''not started''

====Phase 3: Inline Live Examples====

'''Status:''' ''not started''

====Phase 4: Host Gists on WebPlatform.org====

'''Status:''' ''not started''

===Other Tasks===
* Single Sign-On
* Theming to match WebPlatform.org

==Technical Requirements==
===Dedicated Subdomain===
The public URL will be [http://code.webplatform.org code.webplatform.org].

===Additional Subdomains===
In addition to the public-facing URL, Dabblet needs two additional subdomains for security reasons:
* '''Result preview:''' This is only used internally and not displayed to the user. It's a separate domain for security reasons, otherwise people could write dabblets that leak the user's access token. On dabblet.com, this is called preview.dabblet.com
- '''Full-page results:''' This is for results without any dabblet chrome around them. Separate subdomain for the same security reasons. On dabblet, this is result.dabblet.com. This is not critical, worst case we could just disable this feature.