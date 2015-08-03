---
title: WPD:Infrastructure/procedures/Rebuilding Semantic Media Wiki when job queue is going out of control
---
<h1><span class="mw-headline" id="Rebuilding_SMW_when_job_queue_is_going_out_of_control">Rebuilding SMW when job queue is going out of control</span></h1>
<h2><span class="mw-headline" id="Symptom">Symptom</span></h2>
<p>When the job queue seems to always have more and more jobs ("SMWUpdateJob") to do and the job runner ("maintenance/runJobs.php") has more than one running for long periods. It means that the extension needs to rebuild the data from scratch.
</p><p><b>How to validate if it apply?</b>
Look at the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/w/api.php?action=query&amp;meta=siteinfo&amp;siprop=statistics">stats component of MW api</a>. Last event, we had many thousands (e.g. jobs="318102").
</p><p><b>On the database server</b>
From the master, read those values.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">mysql&gt; use wpwiki;
mysql&gt; SELECT COUNT(*) FROM job WHERE job_cmd LIKE '%SMW%';
+----------+
| COUNT(*) |
+----------+
|   318223 |
+----------+</pre></div></div>
<p>Note that number is getting bigger and bigger, it is expectable that they are most likely ALL for Semantic Media Wiki.
</p>
<h2><span class="mw-headline" id="Things_to_know">Things to know</span></h2>
<ul><li> If the database setup has one master and multiple slave, make sure you do them on the master only, the slaves should follow. Doing the opposite might break the consistency of the database cluster.</li>
<li> The cronjobs should ideally, in the scripts, use the timeout utility with a maximum duration of an hour. Doing this prevents to have multiple long running tasks slowly eating all CPU resources.</li>
<li> MediaWiki configuration file (see code below) should show you which is the database master, and which is the read only ("slave"). Only the first entry with <code>load=0</code> can read+write, the other entries are read-only.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">root@app5:/home/renoirb# head -n 40 /srv/webplatform/wiki/CurrentSettings.php
<span class="sc2">&lt;?php</span>
<span class="sc2"><span class="sy0">//</span> ... truncated file notes ...</span>
<span class="sc2">$wgDBservers <span class="sy0">=</span> array<span class="br0">&#40;</span></span>
<span class="sc2">        array<span class="br0">&#40;</span></span>
<span class="sc2">                <span class="st0">'host'</span> <span class="sy0">=</span>&gt;</span> &quot;master.db.wpdn&quot;,        // <span class="sc2">&lt; The salt states ensures</span>
<span class="sc2">                <span class="st0">'dbname'</span> <span class="sy0">=</span>&gt;</span> &quot;wpwiki&quot;,              //     that the master database server
                'user' =&gt; &quot;HIDDENINFORMATION&quot;,     //     has this hostname among all VMs.
                'password' =&gt; &quot;HIDDENINFORMATION&quot;,
                'type' =&gt; &quot;mysql&quot;,
                'flags' =&gt; DBO_DEFAULT,
                'load' =&gt; 0     //  <span class="sc2">&lt; This means read AND write, </span>
<span class="sc2">                                <span class="sy0">//</span>      it is specific to the master.</span>
<span class="sc2">        <span class="br0">&#41;</span>,</span>
<span class="sc2"><span class="br0">&#41;</span>;</span>
<span class="sc2">if <span class="br0">&#40;</span>&#160;!$wgCommandLineMode <span class="br0">&#41;</span> <span class="br0">&#123;</span></span>
<span class="sc2">        $wgDBservers<span class="br0">&#91;</span><span class="br0">&#93;</span> <span class="sy0">=</span> array<span class="br0">&#40;</span></span>
<span class="sc2">                <span class="st0">'host'</span> <span class="sy0">=</span>&gt;</span> &quot;HIDDENINFORMATION.dho.wpdn&quot;,
                'dbname' =&gt; &quot;HIDDENINFORMATION&quot;,
                'user' =&gt; &quot;HIDDENINFORMATION&quot;,
                'password' =&gt; &quot;HIDDENINFORMATION&quot;,
                'type' =&gt; &quot;mysql&quot;,
                'flags' =&gt; DBO_DEFAULT,
                'load' =&gt; 1    //  <span class="sc2">&lt; This means read ONLY</span>
<span class="sc2">        <span class="br0">&#41;</span>;</span>
<span class="sc2"><span class="br0">&#125;</span></span></pre></div></div>
<ul><li> Not all app servers are used full time by the caching layer, Fastly (Varnish). You can see that in <a rel="nofollow" class="external text" href="https://app.fastly.com/">Fastly admin panel</a>, in the "Hosts" within "Configure" for the appropriate service. Current configuration is that two <code>app*</code> VMs have the load in equal portions (200), the 3rd VM is exposed as a backup load (190, see B, in attached image). The 3rd is ready if the two first ones can't serve all requests. </li>
<li> The cronjobs are run from a 4th app server that is not exposed at all. In the <i>app server VM listing</i> below, it's currently "app5".</li></ul>
<p><a href="/wiki/File:fastly-docs-service-hosts-screenshot.png" class="image"><img alt="fastly-docs-service-hosts-screenshot.png" src="//static.webplatform.org/w/public/f/fb/fastly-docs-service-hosts-screenshot.png" width="800" height="634" /></a>
</p>
<ul><li> '<i>app server VM listing</i>. To know which VMs are <code>app*</code> servers, run the following.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">renoirb@deployment:~$ nova list | grep app
| ... | app3  | ACTIVE | None       | Running     | vmnet=10.0.0.32, 208.113.157.171 |
| ... | app4  | ACTIVE | None       | Running     | vmnet=10.0.0.18, 208.113.157.173 |
| ... | app5  | ACTIVE | None       | Running     | vmnet=10.0.0.2, 208.113.157.166  |
| ... | app6  | ACTIVE | None       | Running     | vmnet=10.0.0.14, 208.113.157.162 |</pre></div></div>
<h2><span class="mw-headline" id="Steps">Steps</span></h2>
<h3><span class="mw-headline" id="In_summary">In summary</span></h3>
<ol><li> Make sure the "job runner" will not run during the whole process (e.g. comment all applicable crontab)</li>
<li> Run SMW rebuild command</li>
<li> Truncate job table</li>
<li> Un comment the "job runner"</li></ol>
<h3><span class="mw-headline" id="In_detail">In detail</span></h3>
<ul><li> Find the cron entries mentioning 'runJob.php' and comment them.  This can be found by searching (<code>grep -rli 'runJob' /srv/salt</code>) in the salt state files. The job are assigned to the "<code>www-data</code>" user on the strongest app server (e.g. app4).</li>
<li> Make sure no job is running. The following shows it is fine.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">root@deployment:~# salt 'app*' cmd.run 'ps aux | grep runJob'
app1:
    root     32739  0.0  0.0   9220  1188&#160;?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root     32741  0.0  0.0   6176   672&#160;?        S    00:14   0:00 grep unJob
app6:
    root     10650  0.0  0.0   9220  1188&#160;?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root     10652  0.0  0.0   6180   704&#160;?        S    00:14   0:00 grep unJob
app5:
    www-data 23979  0.0  0.0   4112   580&#160;?        Ss   14:44   0:00 /bin/sh -c /srv/webplatform/wiki/mediawiki-runJobs.sh #1st run
    www-data 23980  0.0  0.0   9228  1332&#160;?        S    14:44   0:00 /bin/bash -l /srv/webplatform/wiki/mediawiki-runJobs.sh
    www-data 23983  0.0  0.0   3876   412&#160;?        Ss   14:44   0:00 /usr/bin/timeout 3100 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    www-data 23984 71.7  0.6 203932 50700&#160;?        R    14:44  24:59 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    www-data 24347  0.0  0.0   4112   584&#160;?        Ss   15:16   0:00 /bin/sh -c /srv/webplatform/wiki/mediawiki-runJobs.sh #2nd run
    www-data 24348  0.0  0.0   9228  1328&#160;?        S    15:16   0:00 /bin/bash -l /srv/webplatform/wiki/mediawiki-runJobs.sh
    www-data 24351  0.0  0.0   3876   412&#160;?        Ss   15:16   0:00 /usr/bin/timeout 3100 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    www-data 24352 69.2  0.5 202424 49160&#160;?        S    15:16   1:59 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    root     24395  0.0  0.0   3876   408 pts/1    S+   15:18   0:00 /usr/bin/timeout 10800 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.ph
p
    root     24396 65.6  0.5 202472 49164 pts/1    R+   15:18   0:13 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    root     24403  0.0  0.0   9220  1188&#160;?        S    15:18   0:00 /bin/sh -c ps aux | grep unJob
    root     24405  0.0  0.0   6180   708&#160;?        S    15:18   0:00 grep unJob
app4:
    root      4183  0.0  0.0   9220  1188&#160;?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root      4185  0.0  0.0   6176   672&#160;?        S    00:14   0:00 grep unJob</pre></div></div>
<ul><li> Note that in this sample, we can see the use of the <code>/usr/bin/timeout</code> with various durations. The current salt configuration has the cronjob to run tasks for a maximum of 3100 seconds. The other job that has a duration of 10800 has been started manually to attempt emptying the queue. </li>
<li> Connect via SSH to the strongest app server with lowest weight in Fastly caching service. It is most likely the one that had crontabs with the <code>'runJob.php'</code> scheduled tasks.</li>
<li> Kill all related process on the server, and make sure they are not running anymore</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">root@app5:/srv/webplatform/wiki/test/extensions/SemanticMediaWiki/maintenance# kill -9 24395 24351 23983
root@app5:/srv/webplatform/wiki/test/extensions/SemanticMediaWiki/maintenance# ps aux | grep unJob
root     32427  0.0  0.0   7640   916 pts/3    S+   02:02   0:00 grep --color=auto unJob</pre></div></div>
<ul><li> Start a <code>screen</code> or <code>tmux</code> session and run the following from within it.  That way, if your SSH connection dies, the script will continue to run.</li>
<li> Go to the appropriate folder where MediaWiki is installed. We have more than one installation, in this situation the appropriate place is in <code>/srv/webplatform/wiki/current/</code>. Always refer to the Salt states on the deployment server in <code>/srv/salt</code></li>
<li> Run the Semantic Media Wiki refreshData script, it might take a while. Expect about 20 minutes of time to wait.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">cd /srv/webplatform/wiki/wpwiki/mediawiki
php extensions/SemanticMediaWiki/maintenance/SMW_refreshData.php -v
...
(29477) Processing ID 29478 ...
(29478) Processing ID 29479 ...
(29479) Processing ID 29480 ...
(29480) Processing ID 29481 ...
(29481) Processing ID 29482 ...
(29482) Processing ID 29483 ...
(29483) Processing ID 29484 ...
(29484) Processing ID 29485 ...
(29485) Processing ID 29486 ...
(29486) Processing ID 29487 ...
29487 IDs refreshed.</pre></div></div>
<ul><li> If the job runner dies, you can use the ID it died on, and re-run the <code>SMW_refreshData.php</code> with the <code>-s</code> option.</li>
<li> When all is done, you can connect to the master database server and truncate the job table. Note that I made sure that the count is the same as I checked before running the <code>SMW_refreshData.php</code>.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">mysql&gt; use wpwiki;
mysql&gt; SELECT COUNT(*) FROM job WHERE job_cmd LIKE '%SMW%';
+----------+
| COUNT(*) |
+----------+
|   318223 |
+----------+
mysql&gt; truncate job;
Query OK, 0 rows affected (0.34 sec)
mysql&gt; SELECT COUNT(*) FROM job WHERE job_cmd LIKE '%SMW%';
+----------+
| COUNT(*) |
+----------+
|        0 |
+----------+
1 row in set (0.00 sec)</pre></div></div>
<ul><li> All should be fine now!</li>
<li> Re-enable the jobRun in the appropriate cron jobs.</li></ul>
<h2><span class="mw-headline" id="Reference">Reference</span></h2>
<ul><li> <a rel="nofollow" class="external text" href="http://semantic-mediawiki.org/wiki/Help:Repairing_SMW's_data">Repairing Semantic Media Wiki data</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.084 seconds
Real time usage: 1.154 seconds
Preprocessor visited node count: 89/1000000
Preprocessor generated node count: 172/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:15667-0!*!*!!*!5!*!esi=1 and timestamp 20150731034114 and revision id 101222
 -->
