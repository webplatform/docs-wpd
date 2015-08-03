---
title: WPD:Infrastructure/procedures/Create a public download archive repository stored directly in DreamObjects
---
<h1><span class="mw-headline" id="Create_a_public_download_archive_repository_stored_directly_in_DreamObjects">Create a public download archive repository stored directly in DreamObjects</span></h1>
<p><b>Status: INCOMPLETE</b>, <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/121">webplatform/ops#121</a></b>
</p><p>The purpose is twofold:
</p>
<ol><li> Allow download of packages in a public repository so that anybody could download archives the infrastructure generates for its maintenance</li>
<li> Leverage our provider infrastructure so we do not move around archives but fetch them from a common location</li></ol>
<p>This would be ideal since we already use a Swift endpoint to store our backups, we could also have it store our web application and Debian (.deb) packages too.
</p>
<h2><span class="mw-headline" id="SCRATCHPAD">SCRATCHPAD</span></h2>
<p>It assumes:
</p>
<ol><li> You have a Swift compatible Object storage</li>
<li> You have a Varnish frontend and can add your own VCL settings</li></ol>
<h3><span class="mw-headline" id="Create_a_bucket">Create a bucket</span></h3>
<p>Make sure the bucket has defaults to public.
In this example we’ll call the bucket "apt", along with a Swift key of the name "wpd-assets:wpd-assets-user" installed.
</p><p>Also, the bucket will have an alias to be called as "apt.webplatform.org" in DreamObjects, but our DNS won’t point to it directly.
</p><p>Instead, it’ll use Varnish as a frontend to Proxy the requests for us and keep a cache for us in case the DreamObjects becomes unavailable.
</p><p><br />
</p>
<h3><span class="mw-headline" id="Install_your_bucket_credentials_in_your_shell_environment">Install your bucket credentials in your shell environment</span></h3>
<p>Generally in `/etc/profile.d/*.sh`
</p>
<pre> cat /etc/profile.d/swift.sh
 # WebPlatform.org uses DreamHosts and their cloud services DreamObjects,
 # here’s how their config looks like.
 export ST_AUTH="<a rel="nofollow" class="external free" href="https://objects.dreamhost.com:443/auth">https://objects.dreamhost.com:443/auth</a>"
 export ST_USER="wpd-assets:wpd-assets-user"
 export ST_KEY="..."
</pre>
<p><br />
</p>
<h3><span class="mw-headline" id="Configure_from_the_Swift_API_to_allow_the_public_to_read_your_bucket">Configure from the Swift API to allow the public to read your bucket</span></h3>
<p>This requires python-swift client and your shell environment variables installed.
If you havent´t restarted a shell session, you can source the shell environment variables yourself like so:
</p>
<pre> source /etc/profile.d/swift.sh
</pre>
<p>Send the following commands:
</p>
<pre> swift post -r '.r:*' apt
</pre>
<p>Technically the <a rel="nofollow" class="external text" href="http://docs.openstack.org/user-guide/content/managing-openstack-object-storage-with-swift-cli.html">OpenStack Swift documentation</a>, at "Create static website" asks to do the following, but we´ll make Varnish do it for us.
</p>
<pre> swift post -m 'web-index: index.html' apt
 swift post -m 'web-listings: true' apt
</pre>
<p><br />
</p>
<h3><span class="mw-headline" id="Configure_your_Varnish_frontend">Configure your Varnish frontend</span></h3>
<p>In the case of WebPlatform, we are using Fastly as a Varnish frontend server.
</p><p>All you need to do on the DNS side is to have a CNAME point to Fastly’s edges servers like so:
</p>
<pre>&#160;; In webplatform.org bind9 zone file
 apt.webplatform.org IN CNAME webplatform.map.fastly.net.
</pre>
<p>In Fastly, create a service with the following details:
</p>
<ul><li> Host: apt.objects.dreamhost.com</li>
<li> Port: 443</li></ul>
<p>Once created, adjust the service configuration, with the following:
</p><p>Note that its in YAML here by habit of the author and isn’t copy-pasateable, the VCL will be below:
</p><p><code>
</p>
<pre> Domains:
   - apt.webplatform.org
 Hosts:
   Backends:
     - Address: apt.objects.dreamhost.com
       Port: 443
       Shielding: (anything goes here)
   Settings:
     Default Settings:
       Default Host: apt.objects.dreamhost.com
     Request Settings:
       - Default host: apt.objects.dreamhost.com
       - X-Forwarded-For: Append
       - Max stale age: 3600
       - Force SSL: Yes
     Content:
       Headers:
         - Type/Action: Request Set
           Destination: url
           Source: "/index.html"
           Request Conditions:
             - Apply If: req.request ~ "GET" &amp;&amp; req.url ~ "^/$"
        - Type/Action: Request Delete
          Destination: http.cookie
          Ignore If Set: Yes
 </code>
</pre>
<p><br />
... should generate a similar VCL configuration:
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="c source-c"><pre class="de1">  sub vcl_recv <span class="br0">&#123;</span>
  <span class="co2">#FASTLY recv</span>
&#160;
     <span class="kw1">if</span> <span class="br0">&#40;</span><span class="sy0">!</span>req.<span class="me1">http</span>.<span class="me1">Fastly</span><span class="sy0">-</span>SSL<span class="br0">&#41;</span> <span class="br0">&#123;</span>
       error <span class="nu0">801</span> <span class="st0">&quot;Force SSL&quot;</span><span class="sy0">;</span>
     <span class="br0">&#125;</span>
&#160;
     <span class="kw1">if</span> <span class="br0">&#40;</span><span class="sy0">!</span>req.<span class="me1">http</span>.<span class="me1">Fastly</span><span class="sy0">-</span>FF<span class="br0">&#41;</span> <span class="br0">&#123;</span>
       <span class="kw1">if</span> <span class="br0">&#40;</span>req.<span class="me1">http</span>.<span class="me1">X</span><span class="sy0">-</span>Forwarded<span class="sy0">-</span>For<span class="br0">&#41;</span> <span class="br0">&#123;</span>
         set req.<span class="me1">http</span>.<span class="me1">Fastly</span><span class="sy0">-</span>Temp<span class="sy0">-</span>XFF <span class="sy0">=</span> req.<span class="me1">http</span>.<span class="me1">X</span><span class="sy0">-</span>Forwarded<span class="sy0">-</span>For <span class="st0">&quot;, &quot;</span> client.<span class="me1">ip</span><span class="sy0">;</span>
       <span class="br0">&#125;</span> <span class="kw1">else</span> <span class="br0">&#123;</span>
         set req.<span class="me1">http</span>.<span class="me1">Fastly</span><span class="sy0">-</span>Temp<span class="sy0">-</span>XFF <span class="sy0">=</span> client.<span class="me1">ip</span><span class="sy0">;</span>
       <span class="br0">&#125;</span>
     <span class="br0">&#125;</span> <span class="kw1">else</span> <span class="br0">&#123;</span>
       set req.<span class="me1">http</span>.<span class="me1">Fastly</span><span class="sy0">-</span>Temp<span class="sy0">-</span>XFF <span class="sy0">=</span> req.<span class="me1">http</span>.<span class="me1">X</span><span class="sy0">-</span>Forwarded<span class="sy0">-</span>For<span class="sy0">;</span>
     <span class="br0">&#125;</span>
&#160;
     set req.<span class="me1">grace</span> <span class="sy0">=</span> 3600s<span class="sy0">;</span>
     set req.<span class="me1">http</span>.<span class="me1">host</span> <span class="sy0">=</span> <span class="st0">&quot;apt.objects.dreamhost.com&quot;</span><span class="sy0">;</span>
&#160;
     <span class="co2"># Remove ANY cookies, we dont need them at all!</span>
     <span class="kw3">remove</span> req.<span class="me1">http</span>.<span class="me1">Cookie</span><span class="sy0">;</span>
     <span class="co2"># Request Condition: If no file requested, make DirectoryIndex ish Prio: 10</span>
     <span class="kw1">if</span><span class="br0">&#40;</span> req.<span class="me1">request</span> ~ <span class="st0">&quot;GET&quot;</span> <span class="sy0">&amp;&amp;</span> req.<span class="me1">url</span> ~ <span class="st0">&quot;^/$&quot;</span> <span class="br0">&#41;</span> <span class="br0">&#123;</span>
        <span class="co2"># Header rewrite to get our own hardcoded directory index file.</span>
        <span class="co2"># ... anyway we change directory contents very rarely.</span>
        set req.<span class="me1">url</span> <span class="sy0">=</span> <span class="st0">&quot;/index.html&quot;</span><span class="sy0">;</span>
     <span class="br0">&#125;</span>
  <span class="br0">&#125;</span>
&#160;
  sub vcl_error <span class="br0">&#123;</span>
  <span class="co2">#FASTLY error</span>
&#160;
    <span class="kw1">if</span> <span class="br0">&#40;</span>obj.<span class="me1">status</span> <span class="sy0">==</span> <span class="nu0">801</span><span class="br0">&#41;</span> <span class="br0">&#123;</span>
       set obj.<span class="me1">status</span> <span class="sy0">=</span> <span class="nu0">301</span><span class="sy0">;</span>
       set obj.<span class="me1">response</span> <span class="sy0">=</span> <span class="st0">&quot;Moved Permanently&quot;</span><span class="sy0">;</span>
       set obj.<span class="me1">http</span>.<span class="me1">Location</span> <span class="sy0">=</span> <span class="st0">&quot;https://&quot;</span> req.<span class="me1">http</span>.<span class="me1">host</span> req.<span class="me1">url</span><span class="sy0">;</span>
       synthetic <span class="br0">&#123;</span><span class="st0">&quot;&quot;</span><span class="br0">&#125;</span><span class="sy0">;</span>
       <span class="kw1">return</span> <span class="br0">&#40;</span>deliver<span class="br0">&#41;</span><span class="sy0">;</span>
    <span class="br0">&#125;</span>
  <span class="br0">&#125;</span></pre></div></div>

<!-- 
NewPP limit report
CPU time usage: 0.037 seconds
Real time usage: 0.039 seconds
Preprocessor visited node count: 32/1000000
Preprocessor generated node count: 76/1000000
Post‐expand include size: 125/2097152 bytes
Template argument size: 6/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    5.081      1 - -total
100.00%    5.081      1 - Template:OperationsTask
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58625-0!*!*!!*!*!*!esi=1 and timestamp 20150731183436 and revision id 101109
 -->
