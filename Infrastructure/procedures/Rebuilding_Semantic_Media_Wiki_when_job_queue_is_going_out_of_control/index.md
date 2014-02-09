= Rebuilding SMW when job queue is going out of control =

== Symtom ==
When the job queue seems to always have more and more jobs ("SMWUpdateJob") to do and the job runner ("maintenance/runJobs.php") has more than one running for long periods. It means that the extension needs to rebuild the data from scratch.

'''How to validate if it apply?'''
Look at the [http://docs.webplatform.org/w/api.php?action=query&meta=siteinfo&siprop=statistics stats component of MW api]. Last event, we had many thousands (e.g. jobs="318102").

'''On the database server'''
From the master, read those values.

<syntaxhighlight>
mysql> use wpwiki;
mysql> SELECT COUNT(*) FROM job WHERE job_cmd LIKE '%SMW%';
+----------+
| COUNT(*) |
+----------+
|   318223 |
+----------+
</syntaxhighlight>

Note that number is getting bigger and bigger, it is expectable that they are most likely ALL for Semantic Media Wiki.

== Things to know ==
* If the database setup has one master and multiple slave, make sure you do them on the master only, the slaves should follow. Doing the opposite might break the consistency of the database cluster.
* The cronjobs should ideally, in the scripts, use the timeout utility with a maximum duration of an hour. Doing this prevents to have multiple long running tasks slowly eating all CPU resources.
* MediaWiki configuration file should show you which is the master database server and slave. Only the first entry can read and write to the database, the other entries are read-only.
<syntaxhighlight>
root@app5:/home/renoirb# head -n 40 /srv/webplatform/wiki/CurrentSettings.php
<?php
// ... truncated file notes ...
$wgDBservers = array(
        array(
                'host' => "master.db.wpdn",
                'dbname' => "wpwiki",
                'user' => "HIDDENINFORMATION",
                'password' => "HIDDENINFORMATION",
                'type' => "mysql",
                'flags' => DBO_DEFAULT,
                'load' => 0,
        ),
);
if ( !$wgCommandLineMode ) {
        $wgDBservers[] = array(
                'host' => "HIDDENINFORMATION.dho.wpdn",
                'dbname' => "HIDDENINFORMATION",
                'user' => "HIDDENINFORMATION",
                'password' => "HIDDENINFORMATION",
                'type' => "mysql",
                'flags' => DBO_DEFAULT,
                'load' => 1,
        );
}
</syntaxhighlight>
# Not all app servers are used full time by the caching layer, Fastly (Varnish). You can see that in Fastly, in the "Hosts" within "Configure" for the appropriate service. Current configuration is that two VMs have the load in equal portion, and a third is available in case the two first cannot meet the requests.
# The app server that generally run the cron job has the lowest traffic

== Steps ==
=== In summary ===
# Make sure the "job runner" will not run during the whole process (e.g. comment all applicable crontab)
# Run SMW rebuild command
# Truncate job table
# Un comment the "job runner"

=== In detail ===

# Find the cron entries mentioning 'runJob.php' and comment them.  This can be found by searching (grep -rli 'runJob' /srv/salt) in the salt state files. The job are assigned to the "www-data" user on the strongest app server (e.g. app4).
# Make sure no job is running. The following shows it is fine.
<syntaxhighlight>
root@deployment:~# salt 'app*' cmd.run 'ps aux | grep runJob'
app1:
    root     32739  0.0  0.0   9220  1188 ?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root     32741  0.0  0.0   6176   672 ?        S    00:14   0:00 grep unJob
app6:
    root     10650  0.0  0.0   9220  1188 ?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root     10652  0.0  0.0   6180   704 ?        S    00:14   0:00 grep unJob
app5:
    root     30615  0.0  0.0   9220  1184 ?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root     30617  0.0  0.0   6176   676 ?        S    00:14   0:00 grep unJob
app4:
    root      4183  0.0  0.0   9220  1188 ?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root      4185  0.0  0.0   6176   672 ?        S    00:14   0:00 grep unJob 
</syntaxhighlight>
# Connect to the strongest app server with lowest