== Summary ==

Using Varnish does not gives caching for free. The configuration still has to be adjusted to each site specifics. Details such as a web application sending HTTP headers with no-cache or max-age=0 can still prevent caching to happen.

This page is about keeping notes on current Varnish configuration files and notes to help maintaining an appropriate caching strategy. 

== NOTES ==
An important detail to remember is that Fastly is using Varnish 2.1.4, their configuration specifics do not support either pipe, ban, nor purging with ACL. 

Also, the way to provide CDN service is with what they call "Shield", it is basically a layer of application that stores a local copy of what is grabbed by a service backend server. That way, before hitting again the backend server, it can get from one of their shield servers first.

VCL is the Varnish Configuration language file, throughout the pannel, we can see two VCL buttons, the one beside the service name and revision is to download the generated VCL, whereas we can also provide our own VCL that must have keywords so the panel adds content to it.

A recommended way to work is to follow '''[https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL-  How do I mix and match Fastly VCL with custom VCL]'''

== Accessing VCL configuration from Fastly ==

[[File:20131121-Fastly-vcl-buttons.png|right]]
To access/overwrite the file in Fastly, go to:
* [https://app.fastly.com/ Fastly pannel], login
* Select targeted site (e.g. ''docs.webplatform.org'')
* Configure tab on top, Configure button
* VCL on the left


=== Current Fastly configuration ===
Make the content of snippet as a file and upload it to the Fastly control pannel.

Each subsection should have each site's ACL configuration.



Please ensure to check differences, and reflect deployed changes here or adjust accordingly.

=== GLOBAL ===
Unless another block exist, this configuration can be used on all services within Fastly

<syntaxHighlight>
#
# See: http://docs.webplatform.org/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration
#
director iphashed client {
  .retries = 5;
  {
    .backend = F_app1;
    .weight = 9;
  }
  {
    .backend = F_app2;
    .weight = 9;
  }
  {
    .backend = F_app3;
    .weight = 7;
  }
  {
    .backend = F_app4;
    .weight = 4;
  }
  {
    .backend = F_app5;
    .weight = 1;
  }
}
 
sub vcl_recv {
#FASTLY recv
 
  set req.backend = iphashed;
  set client.identity = req.http.Fastly-Client-IP;
 
  if (req.request != "HEAD" && req.request != "GET" && req.request != "PURGE") {
    return(pass);
  }
 
  # Pass any requests with the "If-None-Match" header directly.
  if (req.http.If-None-Match)
  { return(pass); }
 
  # normalize Accept-Encoding to reduce vary
  if (req.http.Accept-Encoding) {
    if (req.http.User-Agent ~ "MSIE 6") {
      unset req.http.Accept-Encoding;
    } elsif (req.http.Accept-Encoding ~ "gzip") {
      set req.http.Accept-Encoding = "gzip";
    } elsif (req.http.Accept-Encoding ~ "deflate") {
      set req.http.Accept-Encoding = "deflate";
    } else {
      unset req.http.Accept-Encoding;
    }
  }
  return(lookup);
}
 
 
sub vcl_fetch {
#FASTLY fetch
 
  if ((beresp.status == 500 || beresp.status == 503) && req.restarts < 4 && (req.request == "GET" || req.request == "HEAD")) {
    restart;
  } 

  # ESI support
  set req.esi = true;
  esi;

  # Compatables ESI includes and verbose message
  if(req.url ~ "Special:Compatables") {
    set beresp.ttl = 24h;
    set beresp.http.X-Esi-Message = "This document is targeted to be cached 24h";
  }

  if(req.restarts > 0 ) {
    set beresp.http.Fastly-Restarts = req.restarts;
  }
 
  if (beresp.http.Set-Cookie) {
    set req.http.Fastly-Cachetype = "SETCOOKIE";
    return (pass);
  }
 
  if (beresp.http.Cache-Control ~ "private") {
    set req.http.Fastly-Cachetype = "PRIVATE";
    return (pass);
  }
 
  if (beresp.status == 500 || beresp.status == 503) {
    set req.http.Fastly-Cachetype = "ERROR";
    set beresp.ttl = 1s;
    set beresp.grace = 5s;
    return (deliver);
  }
 
 
  if (beresp.http.Expires || beresp.http.Surrogate-Control ~ "max-age" || beresp.http.Cache-Control ~"(s-maxage|max-age)") {
    # keep the ttl here
  } else {
    # apply the default ttl
    set beresp.ttl = 3600s;
  }
 
  return(deliver);
}
 
sub vcl_hit {
#FASTLY hit
 
  if (!obj.cacheable) {
    return(pass);
  }
  return(deliver);
}
 
sub vcl_miss {
#FASTLY miss
  return(fetch);
}
 
sub vcl_deliver {
#FASTLY deliver
  return(deliver);
}
 
sub vcl_error {
#FASTLY error
}
 
sub vcl_pass {
#FASTLY pass
}
</syntaxHighlight>

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