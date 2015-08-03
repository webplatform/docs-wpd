---
title: WPD:Infrastructure/architecture/Roles and environment level
---
<div style="float:right;width:33%;word-wrap:break-word;clear:both;">
<h3><span class="mw-headline" id="WebPlatform_server_Infrastructure_architecture_menu"><a href="/wiki/WPD:Infrastructure/architecture" title="WPD:Infrastructure/architecture">WebPlatform server Infrastructure architecture menu</a></span></h3>
<div class="subpagelist">
<ul><li> <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">Base configuration of a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">Reports to review status</a></li>
<li> <strong class="selflink">Roles and environment level</strong></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/SSL_certificates" title="WPD:Infrastructure/architecture/SSL certificates">SSL certificates</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/The_salt_master" title="WPD:Infrastructure/architecture/The salt master">The salt master</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish" title="WPD:Infrastructure/architecture/Things to consider when we expose service via Fastly and Varnish">Things to consider when we expose service via Fastly and Varnish</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Useful_commands" title="WPD:Infrastructure/architecture/Useful commands">Useful commands</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">VM roles</a></div></li></ul>
<p><b>See also</b>
</p>
<ul><li> <a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes" title="WPD:Infrastructure/procedures/Deploying code changes">Deploying code changes</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Replacing_a_VM" title="WPD:Infrastructure/procedures/Replacing a VM">Replacing a VM</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration" title="WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration">Maintaining Fastly configuration</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Managing_MySQL_replication" title="WPD:Infrastructure/procedures/Managing MySQL replication">Managing MySQL replication</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it" title="WPD:Infrastructure/procedures/Create new database credentials configure a web application to use it">Create new database credentials and configure a web application to use it</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster" title="WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster">Maintaining ElasticSearch cluster</a></li>
<li> <a href="/wiki/WPD:Infrastructure/procedures/Maintaining_email_services" title="WPD:Infrastructure/procedures/Maintaining email services">Maintaining email services</a></li></ul>
</div>
<h1><span class="mw-headline" id="Roles_and_environment_level">Roles and environment level</span></h1>
<p>Each VM has code and configuration deployed to them depending on two factors; <i>role</i> and environment <i>level</i>. 
</p>
<dl><dt>role</dt>
<dd> defines what gets deployed (e.g. service package, web application, etc).</dd>
<dt>level</dt>
<dd> will ensure deployment specific details (e.g. passwords, keys, SSL certificates, top level domain name, etc) are applied.</dd></dl>
<p>This document describes how we define what configuration and code will be applied on a given VM.
</p>
<h2><span class="mw-headline" id="Roles">Roles</span></h2>
<p>The roles of a VM is defined by its name, more than one role can be assigned on a single VM. 
</p><p>Roles are parsed from the name as a list of role names separated by dashes, minus any number it might find.  If you have a VM name <b>redis-alpha1</b>, the roles will therefore be: [&quot;redis&quot;,&quot;alpha&quot;]
</p><p>Some roles are made to ensure configuration based on design decisions (e.g. detect which database VM is the ones we should send writes to). Other roles are about the web application code we deploy, refer to the section  <a href="/wiki/WPD:Infrastructure/procedures/Deploying_code_changes#Deploying.2Fupdating_a_web_app" title="WPD:Infrastructure/procedures/Deploying code changes">Deploying and/or updating a web app in <b>Deploying code changes</b></a>.
</p><p>For an example of a VM with two roles that doesn’t deploy a web application could be a VM with the name "<b>db5-masterdb</b>" which would be used as the main ("<i>masterdb</i>") database server ("<i>db</i>").  Another example would be a VM with the name "<i>notes</i>" which installs hypothesis.
</p><p>The piece of code that makes the parsing is managed by a small piece of Python code in <code>/srv/salt/_grains/purpose.py</code> (see below) that parses the name.
</p><p>Getting the VM’s <i>roles</i> can be done like this:
</p>
<pre> salt db5-masterdb grains.get roles
 db5-masterdb:
   - db
   - masterdb
</pre>
<p>Making an action only on VMs that has a given role can be done in one command.
</p><p>The following command gives the a NGINX status view each VM that has <i>nginx</i> as a role through <a rel="nofollow" class="external text" href="http://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.nginx.html#salt.modules.nginx.status"><i>Salt Stack</i> <b>nginx.status</b> module</a>, more reports are available in <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status" title="WPD:Infrastructure/architecture/Reports to review status">WPD:Infrastructure/architecture/Reports_to_review_status</a>
</p>
<pre> salt -G 'roles:nginx' nginx.status
 specs-nginx:
   ----------
   accepted:
       3052
   active connections:
       1
   handled:
       3052
   reading:
       0
   requests:
       3045
   waiting:
       0
   writing:
       1
 ...
</pre>
<p><br />
<b>Continue reading about roles in <a href="/wiki/WPD:Infrastructure/architecture/VM_roles" title="WPD:Infrastructure/architecture/VM roles">WPD:Infrastructure/architecture/VM_roles</a></b>
</p>
<h2><span class="mw-headline" id="Level">Level</span></h2>
<p>The "<i>environment level</i>" is defined as a <code>key: value</code> string (e.g. "level: production") in <code>/etc/salt/grains</code>. That file is created when the VM is created using the salt master managed <code>/srv/opsconfig/userdata.txt</code> <b>cloud-init</b> boot script.  
</p><p>Getting the <i>environment level</i> name that the VM knows it has can be done like this:
</p>
<pre> salt vmname grains.get level
 vmname:
   staging
</pre>
<p><b>Tip</b> Its a convention to keep in an OpenStack project ONLY contain ONE environment level. Mixing might cause to confusion and manipulation mistakes.
</p><p><br />
</p>
<h1><span class="mw-headline" id="Related">Related</span></h1>
<h2><span class="mw-headline" id="How_salt_detects_the_roles.3F">How salt detects the roles?</span></h2>
<p>In the  <a rel="nofollow" class="external text" href="https://github.com/webplatform/salt-states">salt-states</a> code repository, generally available in the salt master <code>/srv/salt/_grains/purpose.py</code>. The code looks like this.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="python source-python"><pre class="de1"><span class="co1">#!/usr/bin/env python</span>
&#160;
<span class="kw1">import</span> <span class="kw3">socket</span>
<span class="kw1">from</span> <span class="kw3">string</span> <span class="kw1">import</span> digits
&#160;
hostname <span class="sy0">=</span> <span class="kw3">socket</span>.<span class="me1">gethostname</span><span class="br0">&#40;</span><span class="br0">&#41;</span>.<span class="me1">translate</span><span class="br0">&#40;</span><span class="kw2">None</span><span class="sy0">,</span> digits<span class="br0">&#41;</span>
&#160;
<span class="kw1">def</span> roles<span class="br0">&#40;</span><span class="br0">&#41;</span>:
        <span class="st0">'''
        Parse the host hostname and creates a list of roles
&#160;
        Based on the hostname (without domain name), should return:
&#160;
                salt            -&gt; grain:roles: [&quot;salt&quot;]
                redis-jobs1     -&gt; grain:roles: [&quot;redis&quot;,&quot;jobs&quot;]
&#160;
        '''</span>
        dataObject <span class="sy0">=</span> <span class="br0">&#123;</span><span class="st0">'roles'</span>: hostname.<span class="me1">split</span><span class="br0">&#40;</span><span class="st0">'-'</span><span class="br0">&#41;</span><span class="br0">&#125;</span>
        <span class="kw1">return</span> dataObject</pre></div></div>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58599-0!*!0!!*!*!*!esi=1 and timestamp 20150731185717 and revision id 101523
 -->
