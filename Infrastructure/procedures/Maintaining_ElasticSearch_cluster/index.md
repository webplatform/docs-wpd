---
title: WPD:Infrastructure/procedures/Maintaining ElasticSearch cluster
---
<h1><span class="mw-headline" id="Maintaining_ElasticSearch_cluster">Maintaining ElasticSearch cluster</span></h1>
<p>To get details about how a node is installed, refer to <a href="/wiki/WPD:Infrastructure/architecture/VM_roles#elastic" title="WPD:Infrastructure/architecture/VM roles">WPD:Infrastructure/architecture/VM_roles#elastic</a>
</p>
<h2><span class="mw-headline" id="How_to_get_system_status.2Fhealth">How to get system status/health</span></h2>
<p>Since everything is made through HTTP calls, here are a few we can make.
</p>
<pre>   curl localhost:9200/_cluster/stats?pretty
   curl localhost:9200/_cluster/health?pretty
   curl localhost:9200/_cluster/state?pretty
   curl 'http://localhost:9200/_cluster/health?wait_for_status=green&amp;timeout=50s'
   curl localhost:9200/_nodes/_local?pretty &gt; nodes_details.json
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="How_backups_are_made">How backups are made</span></h2>
<p>Our ElasticSearch cluster backup is currently done through <b>type: fs</b>, each <b>elastic</b> VM mounts an NFS share up to the <b>backup</b> VM.
</p>
<ul><li> <b>backup</b> VM exposes through NFS <code>backup:/srv/exports/elasticsearch</code></li>
<li> <b>elastic</b> VMs sees <b>backup</b>’s NFS mount point at <code>/mnt/backup/elasticsearch/nfsshared</code></li>
<li> ElasticSearch has it configured so that it saves snapshot at <code>/mnt/backup/elasticsearch/nfsshared</code></li>
<li> Every <b>elastic</b> VMs shares <code>/mnt/backup/elasticsearch/nfsshared</code> — This is what the <b>type: fs</b> ElasticSearch snapshot requires</li>
<li> <b>backup</b> VM has a cronjob to create a snapshot at midnight EST (<code>PUT /_snapshot/nfsshared/production</code>)</li>
<li> The snapshot name is based on the deployment level (e.g. "<b>level: staging</b>"), we would see "staging" in stead of "production" as the snapshot name. — We have ONE <b>backup</b> VM per deployment.</li>
<li> <b>backup</b> VM has another cronjob to create an archive of the elastic VMs NFS’ mount points and stores it along with what’s stored in <b>backup</b>’s <code>/mnt/backup</code> backups archive folder</li></ul>
<p>It means that, in <b>production</b> level on the March 11 2015, the following would happen:
</p>
<ol><li> at midnight, the <b>backup</b> VM issues an HTTP request to <b>elastic</b> VM to make a snapshot</li>
<li> ElasticSearch will save the snapshot from any <b>elastic</b> VM as <code>/mnt/backup/elasticsearch/nfsshared/snapshot-production</code> — any elastic VM has the same folder anyway</li>
<li> at 1 am, the <b>backup</b> VM has a cronjob to create an archive
<ol><li> the <b>backup</b> VM makes an archive of the full <code>/srv/exports/elasticsearch/nfsshared</code> — therefore including any other snapshots the cluster might have</li>
<li> the <b>backup</b> VM then saves the archive at <code>/mnt/backup/elasticsearch-snapshot-20150311.tar.gz</code> — along with other backups the VM stores.</li></ol></li></ol>
<p><br />
</p>
<h2><span class="mw-headline" id="Misc_tasks">Misc tasks</span></h2>
<h3><span class="mw-headline" id="Backup_and_restore">Backup and restore</span></h3>
<p>ElasticSearch backup are referred to as "snapshots".
</p><p>Its a two step process;
</p>
<ol><li> where to store the snapshot. It can be locally (type: fs) or using a plugin</li>
<li> make an API call to either create a new snapshot, or restore</li></ol>
<p>A drawback with the <b>type = fs</b> storage is that every ES nodes MUST have access to the same folder through network mount.
This is why we will use another mechanism as soon as possible, the ideal would be to send to a DreamObject bucket directly.
</p><p>First, we have to setup a snapshot location.
</p>
<pre>   curl -XPUT localhost:9200/_snapshot/nfsshared -d '{
     "type": "fs", 
     "settings": {
         "location": "/mnt/backup/elasticsearch/nfsshared",
         "compress": true}}'
</pre>
<p>Idea is that we create (HTTP PUT) a new <b>_snapshot</b> location with alias <b>nfsshared</b> that’ll read/write in <b>/mnt/backup/elasticsearch/nfsshared</b>.
</p><p>Inquire about existing snapshots:
</p>
<pre>   curl localhost:9200/_snapshot/nfsshared/_all?pretty
   {
     "snapshots"&#160;: [ {
       "snapshot"&#160;: "2015030900",
       "indices"&#160;: [ "notes" ],
       "state"&#160;: "SUCCESS",
       "start_time"&#160;: "2015-03-09T23:43:17.971Z",
       "start_time_in_millis"&#160;: 1425944597971,
       "end_time"&#160;: "2015-03-09T23:43:18.451Z",
       "end_time_in_millis"&#160;: 1425944598451,
       "duration_in_millis"&#160;: 480,
       "failures"&#160;: [ ],
       "shards"&#160;: {
         "total"&#160;: 5,
         "failed"&#160;: 0,
         "successful"&#160;: 5
       }
     } ]
   }
</pre>
<p>Recover a snapshot, e.g. "2015030900":
</p>
<pre>   curl -XPOST localhost:9200/_snapshot/nfsshared/2015030900/_restore
</pre>
<p>Create a snapshot:
</p>
<pre>   curl -XPUT localhost:9200/_snapshot/nfsshared/production?wait_for_completion=true
</pre>
<p>Check a snapshot status:
</p>
<pre>   curl localhost:9200/_snapshot/nfsshared/production?pretty
</pre>
<p><br />
</p>
<h4><span class="mw-headline" id="Use_a_plugin_to_store_backups_to_a_Swift_endpoint_automatically">Use a plugin to store backups to a Swift endpoint automatically</span></h4>
<p>This option would be perfect as we wouldn’t need to sync to DreamObjects later like we need to do with the rest.
</p><p>This has to be done, refer to <i>WebPlatform GitHub operations issue tracker</i>, at <b><a rel="nofollow" class="external text" href="https://github.com/webplatform/ops/issues/120">webplatform/ops#120</a></b>. Until then, we’ll stick to initial <a href="#How_backups_are_made">#How backups are made</a>
</p><p><br />
</p><p><br />
</p>
<h4><span class="mw-headline" id="Related_reference">Related reference</span></h4>
<ul><li> <a rel="nofollow" class="external free" href="http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/modules-snapshots.html">http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/modules-snapshots.html</a></li>
<li> <a rel="nofollow" class="external free" href="https://github.com/wikimedia/search-repository-swift">https://github.com/wikimedia/search-repository-swift</a></li></ul>
<p><br />
</p>
<h3><span class="mw-headline" id="Plugins">Plugins</span></h3>
<p>ElasticSearch has many plugins available, we aren’t using any yet.
</p>
<h3><span class="mw-headline" id="Example_on_how_to_install_a_plugin">Example on how to install a plugin</span></h3>
<p>One of the plugins ElasticSearch has is "Marvel", a status dashboard to show the cluster health using Kibana. Kibana is an open source project that’s made to create graphs based on data we can feed it.
</p><p>The following will show how to install "Marvel" as an example on how to install and use an ElasticSearch plugin.
</p><p>To install, you can run from any '<i>elastic</i> node.
</p><p>Technically if we use in production, we’ll ensure they are installed but its out of the scope of this quick procedure.
</p>
<pre>   root@elastic1:~# /usr/share/elasticsearch/bin/plugin -i elasticsearch/marvel/latest
</pre>
<p>This particular plugin exposes a web application at <b>hostname:9200/_plugin/marvel</b>. Here it would be at <b>elastic1:9200/_plugin/marvel</b>.
</p><p>Since our network doesn’t expose everything to the public, if we want to see what it has we’ll have to make a web browser to pass through the salt master SOCKS proxy so we can have our local computer access the <i>elastic1</i> node as if we were in the same network.
</p><p>Details on how to access the dashboard is described in <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH" title="WPD:Infrastructure/architecture/Base configuration of a VM">WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH</a>.
</p><p>Once you have a web browser setup, you can go to "http://elastic1:9200/_plugin/marvel/" and see the dashboard;
</p><p><a href="/wiki/File:elasticsearch-cluster-status-201503.png" class="image"><img alt="elasticsearch-cluster-status-201503.png" src="//static.webplatform.org/w/public/6/61/elasticsearch-cluster-status-201503.png" width="2064" height="1980" /></a>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Reference">Reference</span></h2>
<ul><li> <a rel="nofollow" class="external free" href="http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/modules-plugins.html">http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/modules-plugins.html</a></li>
<li> <a rel="nofollow" class="external text" href="http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-repositories.html">ElasticSearch setup repositories</a></li>
<li> <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH" title="WPD:Infrastructure/architecture/Base configuration of a VM">WebPlatform Infrastructure architecture notes, at "Accessing a VM"</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-service.html">http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-service.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.xmsxmx.com/elasticsearch-cluster-configuration-best-practices/">http://www.xmsxmx.com/elasticsearch-cluster-configuration-best-practices/</a></li></ul>
<h4><span class="mw-headline" id="Understanding_how_ElasticSearch_works">Understanding how ElasticSearch works</span></h4>
<p>A <i>must-read</i> list to help understand how ElasticSearch works. It takes more or less two hours.
</p>
<ul><li> <a rel="nofollow" class="external free" href="http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distributed-search.html">http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distributed-search.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distrib-read.html">http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distrib-read.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distributed-docs.html">http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distributed-docs.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/_scale_horizontally.html">http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/_scale_horizontally.html</a></li>
<li> <a rel="nofollow" class="external free" href="http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/_coping_with_failure.html">http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/_coping_with_failure.html</a></li></ul>

<!-- 
NewPP limit report
CPU time usage: 0.071 seconds
Real time usage: 0.965 seconds
Preprocessor visited node count: 67/1000000
Preprocessor generated node count: 116/1000000
Post‐expand include size: 125/2097152 bytes
Template argument size: 6/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    4.895      1 - -total
100.00%    4.895      1 - Template:OperationsTask
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58623-0!*!0!!*!5!*!esi=1 and timestamp 20150731100143 and revision id 101120
 -->
