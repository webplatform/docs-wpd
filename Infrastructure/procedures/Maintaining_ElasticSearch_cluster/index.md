= Maintaining ElasticSearch cluster =

== How to get system status/health ==

Since everything is made through HTTP calls, here are a few we can make.

    curl localhost:9200/_cluster/stats?pretty
    curl localhost:9200/_cluster/health?pretty
    curl localhost:9200/_cluster/state?pretty
    <nowiki>curl 'http://localhost:9200/_cluster/health?wait_for_status=green&timeout=50s'</nowiki>
    curl localhost:9200/_nodes/_local?pretty > nodes_details.json


== How backups are made ==

Our ElasticSearch cluster backup is currently done through '''type: fs''', each '''elastic''' VM mounts an NFS share up to the '''backup''' VM.

* '''backup''' VM exposes through NFS <code>backup:/srv/exports/elasticsearch</code>
* '''elastic''' VMs sees '''backup'''’s NFS mount point at <code>/mnt/backup/elasticsearch/nfsshared</code>
* ElasticSearch has it configured so that it saves snapshot at <code>/mnt/backup/elasticsearch/nfsshared</code>
* Every '''elastic''' VMs shares <code>/mnt/backup/elasticsearch/nfsshared</code> — This is what the '''type: fs''' ElasticSearch snapshot requires
* '''backup''' VM has a cronjob to create a snapshot at midnight EST (<code>PUT /_snapshot/nfsshared/production</code>)
* The snapshot name is based on the deployment level (e.g. "'''level: staging'''"), we would see "staging" in stead of "production" as the snapshot name. — We have ONE '''backup''' VM per deployment.
* '''backup''' VM has another cronjob to create an archive of the elastic VMs NFS’ mount points and stores it along with what’s stored in '''backup'''’s <code>/mnt/backup</code> backups archive folder

It means that, in '''production''' level on the March 11 2015, the following would happen:
# at midnight, the '''backup''' VM issues an HTTP request to '''elastic''' VM to make a snapshot
# ElasticSearch will save the snapshot from any '''elastic''' VM as <code>/mnt/backup/elasticsearch/nfsshared/snapshot-production</code> — any elastic VM has the same folder anyway
# at 1 am, the '''backup''' VM has a cronjob to create an archive
## the '''backup''' VM makes an archive of the full <code>/srv/exports/elasticsearch/nfsshared</code> — therefore including any other snapshots the cluster might have
## the '''backup''' VM then saves the archive at <code>/mnt/backup/elasticsearch-snapshot-20150311.tar.gz</code> — along with other backups the VM stores.



== Misc tasks ==
=== Backup and restore ===

ElasticSearch backup are referred to as "snapshots".

Its a two step process;

# where to store the snapshot. It can be locally (type: fs) or using a plugin
# make an API call to either create a new snapshot, or restore

A drawback with the '''type = fs''' storage is that every ES nodes MUST have access to the same folder through network mount.
This is why we will use another mechanism as soon as possible, the ideal would be to send to a DreamObject bucket directly.

First, we have to setup a snapshot location.

    curl -XPUT localhost:9200/_snapshot/nfsshared -d '{
      "type": "fs", 
      "settings": {
          "location": "/mnt/backup/elasticsearch/nfsshared",
          "compress": true}}'

Idea is that we create (HTTP PUT) a new '''_snapshot''' location with alias '''nfsshared''' that’ll read/write in '''/mnt/backup/elasticsearch/nfsshared'''.

Inquire about existing snapshots:

    curl localhost:9200/_snapshot/nfsshared/_all?pretty
    {
      "snapshots" : [ {
        "snapshot" : "2015030900",
        "indices" : [ "notes" ],
        "state" : "SUCCESS",
        "start_time" : "2015-03-09T23:43:17.971Z",
        "start_time_in_millis" : 1425944597971,
        "end_time" : "2015-03-09T23:43:18.451Z",
        "end_time_in_millis" : 1425944598451,
        "duration_in_millis" : 480,
        "failures" : [ ],
        "shards" : {
          "total" : 5,
          "failed" : 0,
          "successful" : 5
        }
      } ]
    }

Recover a snapshot, e.g. "2015030900":

    curl -XPOST localhost:9200/_snapshot/nfsshared/2015030900/_restore

Create a snapshot:

    curl -XPUT localhost:9200/_snapshot/nfsshared/production?wait_for_completion=true

Check a snapshot status:

    curl localhost:9200/_snapshot/nfsshared/production?pretty



==== Use a plugin to store backups to a Swift endpoint automatically ====

This option would be perfect as we wouldn’t need to sync to DreamObjects later like we need to do with the rest.

This has to be done, refer to {{OperationsTask|120}}. Until then, we’ll stick to initial [[#How backups are made]]




==== Related reference ====

* http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/modules-snapshots.html
* https://github.com/wikimedia/search-repository-swift


=== Plugins ===

ElasticSearch has many plugins available, we aren’t using any yet.

=== Example on how to install a plugin ===

One of the plugins ElasticSearch has is "Marvel", a status dashboard to show the cluster health using Kibana. Kibana is an open source project that’s made to create graphs based on data we can feed it.

The following will show how to install "Marvel" as an example on how to install and use an ElasticSearch plugin.

To install, you can run from any '''elastic'' node.

Technically if we use in production, we’ll ensure they are installed but its out of the scope of this quick procedure.

    root@elastic1:~# /usr/share/elasticsearch/bin/plugin -i elasticsearch/marvel/latest

This particular plugin exposes a web application at '''hostname:9200/_plugin/marvel'''. Here it would be at '''elastic1:9200/_plugin/marvel'''.

Since our network doesn’t expose everything to the public, if we want to see what it has we’ll have to make a web browser to pass through the salt master SOCKS proxy so we can have our local computer access the ''elastic1'' node as if we were in the same network.

Details on how to access the dashboard is described in [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH]].

Once you have a web browser setup, you can go to "<nowiki>http://elastic1:9200/_plugin/marvel/</nowiki>" and see the dashboard;

[[File:elasticsearch-cluster-status-201503.png]]



== Reference ==

* http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/modules-plugins.html
* [http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-repositories.html ElasticSearch setup repositories]
* [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH|WebPlatform Infrastructure architecture notes, at "Accessing a VM"]]
* http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-service.html
* http://www.xmsxmx.com/elasticsearch-cluster-configuration-best-practices/

==== Understanding how ElasticSearch works ====

A ''must-read'' list to help understand how ElasticSearch works. It takes more or less two hours.

* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distributed-search.html
* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distrib-read.html
* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distributed-docs.html
* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/_scale_horizontally.html
* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/_coping_with_failure.html