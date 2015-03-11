= Maintaining ElasticSearch cluster =
== Backup and restore ==
=== Summary ===

ElasticSearch backup are refered to as "snapshots".

Its a two step process;

1. where to store the snapshot. It can be locally (type: fs) or using a plugin
2. make an API call to either create a new snapshot, or restore

A drawback with the `fs` storage is that every ES nodes MUST have access to the same folder through network mount.
This is why we will use another mechanism as soon as possible, the ideal would be to send to a DreamObject bucket directly.



=== Typical procedure ===

First, we have to setup a snapshot location.

    curl -XPUT localhost:9200/_snapshot/nfsshared -d '{"type": "fs", "settings": {"location": "/mnt/backup/elasticsearch/nfsshared", "compress": true}}'

Idea is that we create (HTTP PUT) a new `_snapshot` location with alias `nfsshared` that’ll read/write in `/mnt/backup/elasticsearch/nfsshared`.

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



=== Backup to Swift using WikiMedia Swift ElasticSearch plugin ===

This option would be perfect as we wouldn’t need to sync to DreamObjects later like we need to do with the rest.

      cd /usr/share/elasticsearch
      ./bin/plugin -i org.wikimedia.elasticsearch.swift/swift-repository-plugin/0.7
      curl -XPUT localhost:9200/_snapshot/swift_backup -d '{"type": "swift", "settings":
                 "swift_url": "https://objects.dreamhost.com:443/auth",
                 "swift_container": "elasticsearch-snapshots",
                 "swift_username": "wpd-ci:salt-master",
                 "swift_password": "zSag2bJqO0zLByix5ApaN1cw9QhxIMsmRI-DYZ2X"}}'



=== Related reference ===

* http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/modules-snapshots.html
* https://github.com/wikimedia/search-repository-swift



== Poking around a cluster ==

    curl localhost:9200/_cluster/stats?pretty
    curl localhost:9200/_cluster/health?pretty
    curl localhost:9200/_cluster/state?pretty
    curl 'http://localhost:9200/_cluster/health?wait_for_status=green&timeout=50s'
    curl localhost:9200/_nodes/_local?pretty > nodes_details.json


== Plugins ==

=== Plugins basics ===

To install, you can run from one node. Technically if we use in production, we’ll ensure they are installed.

    root@elastic3:~# /usr/share/elasticsearch/bin/plugin -i elasticsearch/marvel/latest

Accessing, you can connect through an SSH proxy as its [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH|described in the 2015 architecture documentation sprint at "Accessing a VM using SSH"]]

    http://elastic3:9200/_plugin/marvel/

=== Related reference ===

* http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/modules-plugins.html



== Reference ==

* [http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-repositories.html ElasticSearch setup repositories]
* [[WPD:Infrastructure/architecture/Base_configuration_of_a_VM#Accessing_a_VM_using_SSH|WebPlatform Infrastructure architecture notes, at "Accessing a VM"]]
* http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-service.html
* http://www.xmsxmx.com/elasticsearch-cluster-configuration-best-practices/


=== Understanding how ElasticSearch works ===

* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distributed-search.html
* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distrib-read.html
* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/distributed-docs.html
* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/_scale_horizontally.html
* http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/_coping_with_failure.html