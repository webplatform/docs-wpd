== Summary ==
This page is about keeping notes on current Varnish configuration fils and notes to help maintaining an appropriate caching strategy. 

== Details to remember ==
An important detail to remember is that Fastly is using Varnish 2.1.4, do not support pipe, ban, nor purging with ACL. 

Also, they provide a feature called 'Shield' that is basically an ad-hoc backend that keeps a local copy of what gets cached and is served instead of using the backend, this is what makes it be also act like a CDN.

A recommended way to work is to follow '''[https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL-  How do I mix and match Fastly VCL with custom VCL]'''

== Links ==
* [http://www.mediawiki.org/wiki/Manual:Varnish_caching MediaWiki Varnish Caching]
* [http://labs.creativecommons.org/2011/03/18/caching-mediawiki-with-varnish/ Caching mediawiki with varnish]
* [https://www.varnish-cache.org/lists/pipermail/varnish-misc/2012-January/021574.html Default VCL for MediaWiki]
* [https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL- Fastly: How to mix and match Fastly VCL with custom VCL (Varnish configuration file)]
* [http://kly.no/posts/2010_01_08__Hitpass_objects_and_Varnish__.rst Varnish caching, definition of HIT, PASS and other caching lingo]
* [http://docs.fastly.com/guides/21847086 Fastly: Caching tutorials]
** [http://docs.fastly.com/guides/21835572/21744408 Fastly: Removing headers from backend response]
** [http://docs.fastly.com/guides/21835572/23999817 Fastly: Adding and modifying headers]
** [http://docs.fastly.com/guides/21847086/22257776 How to serve stale content in case of origin becoming unavailable]
* [http://docs.fastly.com/guides/21847086/26628787 Fastly tutorial: Cache control]
* [https://www.varnish-cache.org/docs/2.1/genindex.html Varnish documentation]
** [https://www.varnish-cache.org/docs/2.1/tutorial/vcl.html Varnish configuration language]
** [https://www.varnish-cache.org/docs/2.1/tutorial/cookies.html Varnish tutorial cookies]
* [https://www.varnish-software.com/static/book/Tuning.html?highlight=timeout Varnish book about tuning]

=== Fastly configuration ===
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

  # Compatables ESI includes
  if(req.url ~ "Special:Compatables") {
    esi;
    set beresp.ttl = 24h;
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

=== Testing Page edition ===
<syntaxHighlight lang="bash">
#! /bin/sh
#
# author: Max Polk
#
echo "TEST connecting to a wiki and editing using the api.php interface"
 
# Edit these variables
export WIKI_USERNAME='ZZZ'
export WIKI_PASSWORD='ZZZ'
export WIKI_API='http://docs.webplatform.org/t/api.php'

# Under mac OS, option dry-run doesn't exist, you can do `cat temporaryfile.txt`  and fill a file with test data
export CONTENT='Sample page contents: '$(mktemp --dry-run)

export PAGE='Tests/javascript-a'
export PAGE_URLENCODED='Tests%2Fjavascript-a'
export SUMMARY='Automated test edit'
export LOG_FILE='LOG.txt'
export RESULT_FILE='RESULT.txt'
export COOKIE_FILE='COOKIES.txt'
 
function append ()
{
    echo "$1" >> "$LOG_FILE"
}
 
function appendfile ()
{
    cat "$1" >> "$LOG_FILE"
}
 
function showbanner ()
{
    echo
    echo "----------------------------------------------------------------------"
    echo "$1"
    echo "----------------------------------------------------------------------"
}
 
function showoutput ()
{
    cat "$LOG_FILE"
}
 
#======================================================================
# Login
#======================================================================
 
# New log file for this request
showbanner "Login request"
echo -n > "$LOG_FILE"
 
# Empty the cookie file
echo -n > "$COOKIE_FILE"
append "EMPTIED cookie jar"
append ""
 
# Post request
append "POST to $WIKI_API"
append ""
append "PARAMETERS:"
append "    action=login"
append "    lgname=$WIKI_USERNAME"
append "    lgpassword=$WIKI_PASSWORD"
append "    format=json"
append ""
curl -s --show-error -i "$WIKI_API" -d action=login -d "lgname=$WIKI_USERNAME" -d "lgpassword=$WIKI_PASSWORD" -d format=json -b "$COOKIE_FILE" -c "$COOKIE_FILE" > "$RESULT_FILE"
append "HTTP dump:"
append ""
appendfile "$RESULT_FILE"
append ""
append ""
 
# Verify last result
if ! grep -q '"result":"NeedToken"' "$RESULT_FILE"; then
    append ""
    append 'FAILURE, did not find: "result":"NeedToken"'
    append ""
    append 'EXPECTED something like: {"login":{"result":"NeedToken"'
    showoutput
    exit 1
fi
# Get token from last result
export TOKEN=$(grep "^{" "$RESULT_FILE" | sed 's/^.*"token":"\([^"]*\)".*$/\1/')
if [ -z "$TOKEN" ]; then
    echo "Unable to find token"
    exit 1
fi
append ""
append "EXTRACTED TOKEN:"
append "    $TOKEN"
showoutput
 
#======================================================================
# Verify login using login/token from previous output
#======================================================================
 
# New log file for this request
showbanner "Login verification"
echo -n > "$LOG_FILE"
 
# Post verification
append "POST to $WIKI_API"
append ""
append "PARAMETERS:"
append "    action=login"
append "    lgname=$WIKI_USERNAME"
append "    lgpassword=$WIKI_PASSWORD"
append "    lgtoken=$TOKEN"
append "    format=json"
append ""
curl -s --show-error -i "$WIKI_API" -d action=login -d "lgname=$WIKI_USERNAME" -d "lgpassword=$WIKI_PASSWORD" -d "lgtoken=$TOKEN" -d format=json -b "$COOKIE_FILE" -c "$COOKIE_FILE" > "$RESULT_FILE"
append "HTTP dump:"
append ""
appendfile "$RESULT_FILE"
append ""
append ""
 
# Verify last result
if ! grep -q '"result":"Success"' "$RESULT_FILE"; then
    append ""
    append 'FAILURE, did not find: "result":"Success"'
    append ""
    append 'EXPECTED something like: {"login":{"result":"Success"'
    showoutput
    exit 1
fi
 
append ""
append "SUCCESSFULLY VERIFIED LOGIN"
showoutput
 
#======================================================================
# Get an edit token
#======================================================================
 
# New log file for this request
showbanner "Obtain edit token"
echo -n > "$LOG_FILE"
 
# Query for edit token
append "GET from $WIKI_API"
append ""
append "PARAMETERS:"
append "    action=query"
append "    prop=info"
append "    intoken=edit"
append "    titles=${PAGE}"
append "    format=json"
append ""
append "ACTUAL URL:"
append "    ${WIKI_API}?action=query&prop=info&intoken=edit&titles=${PAGE_URLENCODED}&format=json"
append ""
curl -s --show-error -i "${WIKI_API}?action=query&prop=info&intoken=edit&titles=${PAGE_URLENCODED}&format=json" -b "$COOKIE_FILE" -c "$COOKIE_FILE" > "$RESULT_FILE"
append "HTTP dump:"
append ""
appendfile "$RESULT_FILE"
append ""
append ""
 
# Verify last result
if ! grep -q '{"query":{"pages"' "$RESULT_FILE"; then
    append ""
    append 'FAILURE, did not find: {"query":{"pages"'
    append ""
    showoutput
    exit 1
fi
 
# Get edit token from last result (unescape JSON "\\" into "\")
export EDIT_TOKEN=$(grep "^{" "$RESULT_FILE" | sed 's/^.*"edittoken":"\([^"]*\)".*$/\1/' | sed 's/\\\\/\\/g')
if [ -z "$EDIT_TOKEN" ]; then
    echo "Unable to find edit token"
    exit 1
fi
append ""
append "EXTRACTED EDIT TOKEN:"
append "    $EDIT_TOKEN"
showoutput
 
#======================================================================
# Perform actual page edit
#======================================================================
 
# New log file for this request
showbanner "Perform page edit"
echo -n > "$LOG_FILE"
 
# Post edit
append "POST to $WIKI_API"
append ""
append "PARAMETERS:"
append "    action=edit"
append "    title=${PAGE}"
append "    summary=${SUMMARY}"
append "    text=${CONTENT}"
append "    bot=1"
append "    watchlist=nochange"
append "    token=${EDIT_TOKEN}"
append "    format=json"
append ""
curl -s --show-error -i "${WIKI_API}" -d action=edit -d "title=$PAGE" -d "summary=$SUMMARY" -d "text=$CONTENT" -d bot=1 -d watchlist=nochange --data-urlencode "token=$EDIT_TOKEN" -d format=json -b "$COOKIE_FILE" -c "$COOKIE_FILE" > "$RESULT_FILE"
append "HTTP dump:"
append ""
appendfile "$RESULT_FILE"
append ""
append ""
 
# Verify last result
if ! grep -q '"result":"Success"' "$RESULT_FILE"; then
    append ""
    append 'FAILURE, did not find: "result":"Success"'
    append ""
    append 'EXPECTED something like: {"login":{"result":"Success"'
    showoutput
    exit 1
fi
 
showoutput
 
#======================================================================
# Logout
#======================================================================
 
# New log file for this request
showbanner "Logout"
echo -n > "$LOG_FILE"
 
# Post logout
append "POST to $WIKI_API"
append ""
append "PARAMETERS:"
append "    action=logout"
append "    format=json"
append ""
curl -s --show-error -i "$WIKI_API" -d action=logout -d format=json -b "$COOKIE_FILE" -c "$COOKIE_FILE" > "$RESULT_FILE"
append "HTTP dump:"
append ""
appendfile "$RESULT_FILE"
append ""
append ""
 
# Verify last result
if ! grep -q "\[\]" "$RESULT_FILE"; then
    append ""
    append "FAILURE, did not find: \[\]"
    append ""
    showoutput
    exit 1
fi
 
append ""
append "SUCCESSFULLY LOGGED OUT"
showoutput
 
#======================================================================
# Success
#======================================================================
 
showbanner "SUCCESS"
</syntaxHighlight>