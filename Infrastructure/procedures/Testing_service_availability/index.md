---
title: WPD:Infrastructure/procedures/Testing service availability
---
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>Collection of small shell scripts that will be used to test components of the infrastructure.
</p>
<h2><span class="mw-headline" id="By_technology">By technology</span></h2>
<h3><span class="mw-headline" id="PHP_Memcache_library_connection_to_Memcache_cluster">PHP Memcache library connection to Memcache cluster</span></h3>
<pre>   $params = array(
            'class'      =&gt; 'MemcachedPeclBagOStuff',
            'serializer' =&gt; 'php',
            'servers'    =&gt; array(
                    '10.1.1.1:11211',
                    '10.2.2.2:11211',
            ),
            'timeout' =&gt; 250000,
            'connect_timeout' =&gt; 300
   );
   $client = new Memcached;
   $client-&gt;setOption( Memcached::OPT_CONNECT_TIMEOUT, $params['connect_timeout'] * 1000 );
   $client-&gt;setOption( Memcached::OPT_SEND_TIMEOUT, $params['timeout'] );
   $client-&gt;setOption( Memcached::OPT_RECV_TIMEOUT, $params['timeout'] );
   $client-&gt;setOption( Memcached::OPT_POLL_TIMEOUT, $params['timeout'] / 1000 );
   $client-&gt;setOption( Memcached::OPT_LIBKETAMA_COMPATIBLE, true );
   $client-&gt;setOption( Memcached::OPT_SERIALIZER, Memcached::SERIALIZER_PHP );
   //require('/srv/webplatform/wiki/current/includes/GlobalFunctions.php');
   require('/srv/webplatform/wiki/current/includes/IP.php');
   //require('/srv/webplatform/wiki/current/includes/objectcache/MemcachedPeclBagOStuff.php');
   $servers = array();
   foreach ( $params['servers'] as $host ) {
       $servers[] = IP::splitHostAndPort( $host ); // (ip, port)
   }
   $client-&gt;addServers( $servers );
   $tmp_object = new stdClass;
   $tmp_object-&gt;str_attr = 'test';
   $tmp_object-&gt;int_attr = 123;
   $tmp_object-&gt;date = new DateTime();
   $client-&gt;add('key1', $tmp_object, 10) or die ("Failed to save data at the server");
   var_dump($client-&gt;get('key1'));
   var_dump($client-&gt;get('wpwiki:user:stats:359'));
</pre>
<p><br />
</p>
<h3><span class="mw-headline" id="Website_vhost">Website vhost</span></h3>
<ul><li> One per vhost</li>
<li> Grep if a string exist</li>
<li> Return non zero if it fails</li>
<li> See for <a rel="nofollow" class="external text" href="http://nagiosplugins.org/man/check_http">Nagios check_http</a></li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">    #!/bin/bash
    curl -I -H 'Host: docs.webplatform.org' http://15.185.116.171/wiki/Main_Page?t=cli-renoirb</pre></div></div>
<p><br />
</p>
<h3><span class="mw-headline" id="Adding_pages_through_MediaWiki_API">Adding pages through MediaWiki API</span></h3>
<p><b>Dependencies</b>:
</p>
<ul><li> Varnish configuration do not send cached documents as a reply to a POST request, see <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration</a></li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="bash source-bash"><pre class="de1"><span class="co0">#! /bin/sh</span>
<span class="co0">#</span>
<span class="co0"># author: Max Polk</span>
<span class="co0">#</span>
<span class="kw3">echo</span> <span class="st0">&quot;TEST connecting to a wiki and editing using the api.php interface&quot;</span>
&#160;
<span class="co0"># Edit these variables</span>
<span class="kw3">export</span> <span class="re2">WIKI_USERNAME</span>=<span class="st_h">'ZZZ'</span>
<span class="kw3">export</span> <span class="re2">WIKI_PASSWORD</span>=<span class="st_h">'ZZZ'</span>
<span class="kw3">export</span> <span class="re2">WIKI_API</span>=<span class="st_h">'http://docs.webplatform.org/t/api.php'</span>
&#160;
<span class="co0"># Under mac OS, option dry-run doesn't exist, you can do `cat temporaryfile.txt`  and fill a file with test data</span>
<span class="kw3">export</span> <span class="re2">CONTENT</span>=<span class="st_h">'Sample page contents: '</span>$<span class="br0">&#40;</span><span class="kw2">mktemp</span> --dry-run<span class="br0">&#41;</span>
&#160;
<span class="kw3">export</span> <span class="re2">PAGE</span>=<span class="st_h">'Tests/javascript-a'</span>
<span class="kw3">export</span> <span class="re2">PAGE_URLENCODED</span>=<span class="st_h">'Tests%2Fjavascript-a'</span>
<span class="kw3">export</span> <span class="re2">SUMMARY</span>=<span class="st_h">'Automated test edit'</span>
<span class="kw3">export</span> <span class="re2">LOG_FILE</span>=<span class="st_h">'LOG.txt'</span>
<span class="kw3">export</span> <span class="re2">RESULT_FILE</span>=<span class="st_h">'RESULT.txt'</span>
<span class="kw3">export</span> <span class="re2">COOKIE_FILE</span>=<span class="st_h">'COOKIES.txt'</span>
&#160;
<span class="kw1">function</span> append <span class="br0">&#40;</span><span class="br0">&#41;</span>
<span class="br0">&#123;</span>
    <span class="kw3">echo</span> <span class="st0">&quot;$1&quot;</span> <span class="sy0">&gt;&gt;</span> <span class="st0">&quot;<span class="es2">$LOG_FILE</span>&quot;</span>
<span class="br0">&#125;</span>
&#160;
<span class="kw1">function</span> appendfile <span class="br0">&#40;</span><span class="br0">&#41;</span>
<span class="br0">&#123;</span>
    <span class="kw2">cat</span> <span class="st0">&quot;$1&quot;</span> <span class="sy0">&gt;&gt;</span> <span class="st0">&quot;<span class="es2">$LOG_FILE</span>&quot;</span>
<span class="br0">&#125;</span>
&#160;
<span class="kw1">function</span> showbanner <span class="br0">&#40;</span><span class="br0">&#41;</span>
<span class="br0">&#123;</span>
    <span class="kw3">echo</span>
    <span class="kw3">echo</span> <span class="st0">&quot;----------------------------------------------------------------------&quot;</span>
    <span class="kw3">echo</span> <span class="st0">&quot;$1&quot;</span>
    <span class="kw3">echo</span> <span class="st0">&quot;----------------------------------------------------------------------&quot;</span>
<span class="br0">&#125;</span>
&#160;
<span class="kw1">function</span> showoutput <span class="br0">&#40;</span><span class="br0">&#41;</span>
<span class="br0">&#123;</span>
    <span class="kw2">cat</span> <span class="st0">&quot;<span class="es2">$LOG_FILE</span>&quot;</span>
<span class="br0">&#125;</span>
&#160;
<span class="co0">#======================================================================</span>
<span class="co0"># Login</span>
<span class="co0">#======================================================================</span>
&#160;
<span class="co0"># New log file for this request</span>
showbanner <span class="st0">&quot;Login request&quot;</span>
<span class="kw3">echo</span> <span class="re5">-n</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$LOG_FILE</span>&quot;</span>
&#160;
<span class="co0"># Empty the cookie file</span>
<span class="kw3">echo</span> <span class="re5">-n</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span>
append <span class="st0">&quot;EMPTIED cookie jar&quot;</span>
append <span class="st0">&quot;&quot;</span>
&#160;
<span class="co0"># Post request</span>
append <span class="st0">&quot;POST to <span class="es2">$WIKI_API</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;PARAMETERS:&quot;</span>
append <span class="st0">&quot;    action=login&quot;</span>
append <span class="st0">&quot;    lgname=<span class="es2">$WIKI_USERNAME</span>&quot;</span>
append <span class="st0">&quot;    lgpassword=<span class="es2">$WIKI_PASSWORD</span>&quot;</span>
append <span class="st0">&quot;    format=json&quot;</span>
append <span class="st0">&quot;&quot;</span>
curl <span class="re5">-s</span> <span class="re5">--show-error</span> <span class="re5">-i</span> <span class="st0">&quot;<span class="es2">$WIKI_API</span>&quot;</span> <span class="re5">-d</span> <span class="re2">action</span>=<span class="kw2">login</span> <span class="re5">-d</span> <span class="st0">&quot;lgname=<span class="es2">$WIKI_USERNAME</span>&quot;</span> <span class="re5">-d</span> <span class="st0">&quot;lgpassword=<span class="es2">$WIKI_PASSWORD</span>&quot;</span> <span class="re5">-d</span> <span class="re2">format</span>=json <span class="re5">-b</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="re5">-c</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;HTTP dump:&quot;</span>
append <span class="st0">&quot;&quot;</span>
appendfile <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;&quot;</span>
&#160;
<span class="co0"># Verify last result</span>
<span class="kw1">if</span> <span class="sy0">!</span> <span class="kw2">grep</span> <span class="re5">-q</span> <span class="st_h">'&quot;result&quot;:&quot;NeedToken&quot;'</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>; <span class="kw1">then</span>
    append <span class="st0">&quot;&quot;</span>
    append <span class="st_h">'FAILURE, did not find: &quot;result&quot;:&quot;NeedToken&quot;'</span>
    append <span class="st0">&quot;&quot;</span>
    append <span class="st_h">'EXPECTED something like: {&quot;login&quot;:{&quot;result&quot;:&quot;NeedToken&quot;'</span>
    showoutput
    <span class="kw3">exit</span> <span class="nu0">1</span>
<span class="kw1">fi</span>
<span class="co0"># Get token from last result</span>
<span class="kw3">export</span> <span class="re2">TOKEN</span>=$<span class="br0">&#40;</span><span class="kw2">grep</span> <span class="st0">&quot;^{&quot;</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span> <span class="sy0">|</span> <span class="kw2">sed</span> <span class="st_h">'s/^.*&quot;token&quot;:&quot;\([^&quot;]*\)&quot;.*$/\1/'</span><span class="br0">&#41;</span>
<span class="kw1">if</span> <span class="br0">&#91;</span> <span class="re5">-z</span> <span class="st0">&quot;<span class="es2">$TOKEN</span>&quot;</span> <span class="br0">&#93;</span>; <span class="kw1">then</span>
    <span class="kw3">echo</span> <span class="st0">&quot;Unable to find token&quot;</span>
    <span class="kw3">exit</span> <span class="nu0">1</span>
<span class="kw1">fi</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;EXTRACTED TOKEN:&quot;</span>
append <span class="st0">&quot;    <span class="es2">$TOKEN</span>&quot;</span>
showoutput
&#160;
<span class="co0">#======================================================================</span>
<span class="co0"># Verify login using login/token from previous output</span>
<span class="co0">#======================================================================</span>
&#160;
<span class="co0"># New log file for this request</span>
showbanner <span class="st0">&quot;Login verification&quot;</span>
<span class="kw3">echo</span> <span class="re5">-n</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$LOG_FILE</span>&quot;</span>
&#160;
<span class="co0"># Post verification</span>
append <span class="st0">&quot;POST to <span class="es2">$WIKI_API</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;PARAMETERS:&quot;</span>
append <span class="st0">&quot;    action=login&quot;</span>
append <span class="st0">&quot;    lgname=<span class="es2">$WIKI_USERNAME</span>&quot;</span>
append <span class="st0">&quot;    lgpassword=<span class="es2">$WIKI_PASSWORD</span>&quot;</span>
append <span class="st0">&quot;    lgtoken=<span class="es2">$TOKEN</span>&quot;</span>
append <span class="st0">&quot;    format=json&quot;</span>
append <span class="st0">&quot;&quot;</span>
curl <span class="re5">-s</span> <span class="re5">--show-error</span> <span class="re5">-i</span> <span class="st0">&quot;<span class="es2">$WIKI_API</span>&quot;</span> <span class="re5">-d</span> <span class="re2">action</span>=<span class="kw2">login</span> <span class="re5">-d</span> <span class="st0">&quot;lgname=<span class="es2">$WIKI_USERNAME</span>&quot;</span> <span class="re5">-d</span> <span class="st0">&quot;lgpassword=<span class="es2">$WIKI_PASSWORD</span>&quot;</span> <span class="re5">-d</span> <span class="st0">&quot;lgtoken=<span class="es2">$TOKEN</span>&quot;</span> <span class="re5">-d</span> <span class="re2">format</span>=json <span class="re5">-b</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="re5">-c</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;HTTP dump:&quot;</span>
append <span class="st0">&quot;&quot;</span>
appendfile <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;&quot;</span>
&#160;
<span class="co0"># Verify last result</span>
<span class="kw1">if</span> <span class="sy0">!</span> <span class="kw2">grep</span> <span class="re5">-q</span> <span class="st_h">'&quot;result&quot;:&quot;Success&quot;'</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>; <span class="kw1">then</span>
    append <span class="st0">&quot;&quot;</span>
    append <span class="st_h">'FAILURE, did not find: &quot;result&quot;:&quot;Success&quot;'</span>
    append <span class="st0">&quot;&quot;</span>
    append <span class="st_h">'EXPECTED something like: {&quot;login&quot;:{&quot;result&quot;:&quot;Success&quot;'</span>
    showoutput
    <span class="kw3">exit</span> <span class="nu0">1</span>
<span class="kw1">fi</span>
&#160;
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;SUCCESSFULLY VERIFIED LOGIN&quot;</span>
showoutput
&#160;
<span class="co0">#======================================================================</span>
<span class="co0"># Get an edit token</span>
<span class="co0">#======================================================================</span>
&#160;
<span class="co0"># New log file for this request</span>
showbanner <span class="st0">&quot;Obtain edit token&quot;</span>
<span class="kw3">echo</span> <span class="re5">-n</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$LOG_FILE</span>&quot;</span>
&#160;
<span class="co0"># Query for edit token</span>
append <span class="st0">&quot;GET from <span class="es2">$WIKI_API</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;PARAMETERS:&quot;</span>
append <span class="st0">&quot;    action=query&quot;</span>
append <span class="st0">&quot;    prop=info&quot;</span>
append <span class="st0">&quot;    intoken=edit&quot;</span>
append <span class="st0">&quot;    titles=<span class="es3">${PAGE}</span>&quot;</span>
append <span class="st0">&quot;    format=json&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;ACTUAL URL:&quot;</span>
append <span class="st0">&quot;    <span class="es3">${WIKI_API}</span>?action=query&amp;prop=info&amp;intoken=edit&amp;titles=<span class="es3">${PAGE_URLENCODED}</span>&amp;format=json&quot;</span>
append <span class="st0">&quot;&quot;</span>
curl <span class="re5">-s</span> <span class="re5">--show-error</span> <span class="re5">-i</span> <span class="st0">&quot;<span class="es3">${WIKI_API}</span>?action=query&amp;prop=info&amp;intoken=edit&amp;titles=<span class="es3">${PAGE_URLENCODED}</span>&amp;format=json&quot;</span> <span class="re5">-b</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="re5">-c</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;HTTP dump:&quot;</span>
append <span class="st0">&quot;&quot;</span>
appendfile <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;&quot;</span>
&#160;
<span class="co0"># Verify last result</span>
<span class="kw1">if</span> <span class="sy0">!</span> <span class="kw2">grep</span> <span class="re5">-q</span> <span class="st_h">'{&quot;query&quot;:{&quot;pages&quot;'</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>; <span class="kw1">then</span>
    append <span class="st0">&quot;&quot;</span>
    append <span class="st_h">'FAILURE, did not find: {&quot;query&quot;:{&quot;pages&quot;'</span>
    append <span class="st0">&quot;&quot;</span>
    showoutput
    <span class="kw3">exit</span> <span class="nu0">1</span>
<span class="kw1">fi</span>
&#160;
<span class="co0"># Get edit token from last result (unescape JSON &quot;\\&quot; into &quot;\&quot;)</span>
<span class="kw3">export</span> <span class="re2">EDIT_TOKEN</span>=$<span class="br0">&#40;</span><span class="kw2">grep</span> <span class="st0">&quot;^{&quot;</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span> <span class="sy0">|</span> <span class="kw2">sed</span> <span class="st_h">'s/^.*&quot;edittoken&quot;:&quot;\([^&quot;]*\)&quot;.*$/\1/'</span> <span class="sy0">|</span> <span class="kw2">sed</span> <span class="st_h">'s/\\\\/\\/g'</span><span class="br0">&#41;</span>
<span class="kw1">if</span> <span class="br0">&#91;</span> <span class="re5">-z</span> <span class="st0">&quot;<span class="es2">$EDIT_TOKEN</span>&quot;</span> <span class="br0">&#93;</span>; <span class="kw1">then</span>
    <span class="kw3">echo</span> <span class="st0">&quot;Unable to find edit token&quot;</span>
    <span class="kw3">exit</span> <span class="nu0">1</span>
<span class="kw1">fi</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;EXTRACTED EDIT TOKEN:&quot;</span>
append <span class="st0">&quot;    <span class="es2">$EDIT_TOKEN</span>&quot;</span>
showoutput
&#160;
<span class="co0">#======================================================================</span>
<span class="co0"># Perform actual page edit</span>
<span class="co0">#======================================================================</span>
&#160;
<span class="co0"># New log file for this request</span>
showbanner <span class="st0">&quot;Perform page edit&quot;</span>
<span class="kw3">echo</span> <span class="re5">-n</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$LOG_FILE</span>&quot;</span>
&#160;
<span class="co0"># Post edit</span>
append <span class="st0">&quot;POST to <span class="es2">$WIKI_API</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;PARAMETERS:&quot;</span>
append <span class="st0">&quot;    action=edit&quot;</span>
append <span class="st0">&quot;    title=<span class="es3">${PAGE}</span>&quot;</span>
append <span class="st0">&quot;    summary=<span class="es3">${SUMMARY}</span>&quot;</span>
append <span class="st0">&quot;    text=<span class="es3">${CONTENT}</span>&quot;</span>
append <span class="st0">&quot;    bot=1&quot;</span>
append <span class="st0">&quot;    watchlist=nochange&quot;</span>
append <span class="st0">&quot;    token=<span class="es3">${EDIT_TOKEN}</span>&quot;</span>
append <span class="st0">&quot;    format=json&quot;</span>
append <span class="st0">&quot;&quot;</span>
curl <span class="re5">-s</span> <span class="re5">--show-error</span> <span class="re5">-i</span> <span class="st0">&quot;<span class="es3">${WIKI_API}</span>&quot;</span> <span class="re5">-d</span> <span class="re2">action</span>=edit <span class="re5">-d</span> <span class="st0">&quot;title=<span class="es2">$PAGE</span>&quot;</span> <span class="re5">-d</span> <span class="st0">&quot;summary=<span class="es2">$SUMMARY</span>&quot;</span> <span class="re5">-d</span> <span class="st0">&quot;text=<span class="es2">$CONTENT</span>&quot;</span> <span class="re5">-d</span> <span class="re2">bot</span>=<span class="nu0">1</span> <span class="re5">-d</span> <span class="re2">watchlist</span>=nochange <span class="re5">--data-urlencode</span> <span class="st0">&quot;token=<span class="es2">$EDIT_TOKEN</span>&quot;</span> <span class="re5">-d</span> <span class="re2">format</span>=json <span class="re5">-b</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="re5">-c</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;HTTP dump:&quot;</span>
append <span class="st0">&quot;&quot;</span>
appendfile <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;&quot;</span>
&#160;
<span class="co0"># Verify last result</span>
<span class="kw1">if</span> <span class="sy0">!</span> <span class="kw2">grep</span> <span class="re5">-q</span> <span class="st_h">'&quot;result&quot;:&quot;Success&quot;'</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>; <span class="kw1">then</span>
    append <span class="st0">&quot;&quot;</span>
    append <span class="st_h">'FAILURE, did not find: &quot;result&quot;:&quot;Success&quot;'</span>
    append <span class="st0">&quot;&quot;</span>
    append <span class="st_h">'EXPECTED something like: {&quot;login&quot;:{&quot;result&quot;:&quot;Success&quot;'</span>
    showoutput
    <span class="kw3">exit</span> <span class="nu0">1</span>
<span class="kw1">fi</span>
&#160;
showoutput
&#160;
<span class="co0">#======================================================================</span>
<span class="co0"># Logout</span>
<span class="co0">#======================================================================</span>
&#160;
<span class="co0"># New log file for this request</span>
showbanner <span class="st0">&quot;Logout&quot;</span>
<span class="kw3">echo</span> <span class="re5">-n</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$LOG_FILE</span>&quot;</span>
&#160;
<span class="co0"># Post logout</span>
append <span class="st0">&quot;POST to <span class="es2">$WIKI_API</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;PARAMETERS:&quot;</span>
append <span class="st0">&quot;    action=logout&quot;</span>
append <span class="st0">&quot;    format=json&quot;</span>
append <span class="st0">&quot;&quot;</span>
curl <span class="re5">-s</span> <span class="re5">--show-error</span> <span class="re5">-i</span> <span class="st0">&quot;<span class="es2">$WIKI_API</span>&quot;</span> <span class="re5">-d</span> <span class="re2">action</span>=<span class="kw3">logout</span> <span class="re5">-d</span> <span class="re2">format</span>=json <span class="re5">-b</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="re5">-c</span> <span class="st0">&quot;<span class="es2">$COOKIE_FILE</span>&quot;</span> <span class="sy0">&gt;</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;HTTP dump:&quot;</span>
append <span class="st0">&quot;&quot;</span>
appendfile <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;&quot;</span>
&#160;
<span class="co0"># Verify last result</span>
<span class="kw1">if</span> <span class="sy0">!</span> <span class="kw2">grep</span> <span class="re5">-q</span> <span class="st0">&quot;\[\]&quot;</span> <span class="st0">&quot;<span class="es2">$RESULT_FILE</span>&quot;</span>; <span class="kw1">then</span>
    append <span class="st0">&quot;&quot;</span>
    append <span class="st0">&quot;FAILURE, did not find: \[\]&quot;</span>
    append <span class="st0">&quot;&quot;</span>
    showoutput
    <span class="kw3">exit</span> <span class="nu0">1</span>
<span class="kw1">fi</span>
&#160;
append <span class="st0">&quot;&quot;</span>
append <span class="st0">&quot;SUCCESSFULLY LOGGED OUT&quot;</span>
showoutput
&#160;
<span class="co0">#======================================================================</span>
<span class="co0"># Success</span>
<span class="co0">#======================================================================</span>
&#160;
showbanner <span class="st0">&quot;SUCCESS&quot;</span></pre></div></div>

<!-- 
NewPP limit report
CPU time usage: 0.106 seconds
Real time usage: 0.109 seconds
Preprocessor visited node count: 30/1000000
Preprocessor generated node count: 64/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:10368-0!*!0!!*!*!*!esi=1 and timestamp 20150731121038 and revision id 41291
 -->
