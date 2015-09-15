---
title: Rebuilding SMW when job queue is going out of control
uri: 'WPD:Infrastructure/procedures/Rebuilding Semantic Media Wiki when job queue is going out of control'

---
## <span>Symptom</span>

When the job queue seems to always have more and more jobs ("SMWUpdateJob") to do and the job runner ("maintenance/runJobs.php") has more than one running for long periods. It means that the extension needs to rebuild the data from scratch.

**How to validate if it apply?** Look at the [stats component of MW api](http://docs.webplatform.org/w/api.php?action=query&meta=siteinfo&siprop=statistics). Last event, we had many thousands (e.g. jobs="318102").

**On the database server** From the master, read those values.

``` html
mysql> use wpwiki;
mysql> SELECT COUNT(*) FROM job WHERE job_cmd LIKE '%SMW%';
+----------+
| COUNT(*) |
+----------+
|   318223 |
+----------+
```

 Note that number is getting bigger and bigger, it is expectable that they are most likely ALL for Semantic Media Wiki.

## <span>Things to know</span>

-   If the database setup has one master and multiple slave, make sure you do them on the master only, the slaves should follow. Doing the opposite might break the consistency of the database cluster.
-   The cronjobs should ideally, in the scripts, use the timeout utility with a maximum duration of an hour. Doing this prevents to have multiple long running tasks slowly eating all CPU resources.
-   MediaWiki configuration file (see code below) should show you which is the database master, and which is the read only ("slave"). Only the first entry with `load=0` can read+write, the other entries are read-only.

``` html
root@app5:/home/renoirb# head -n 40 /srv/webplatform/wiki/CurrentSettings.php
<?php
// ... truncated file notes ...
$wgDBservers = array(
        array(
                'host' => "master.db.wpdn",        // < The salt states ensures
                'dbname' => "wpwiki",              //     that the master database server
                'user' => "HIDDENINFORMATION",     //     has this hostname among all VMs.
                'password' => "HIDDENINFORMATION",
                'type' => "mysql",
                'flags' => DBO_DEFAULT,
                'load' => 0     //  < This means read AND write,
                                //      it is specific to the master.
        ),
);
if ( !$wgCommandLineMode ) {
        $wgDBservers[] = array(
                'host' => "HIDDENINFORMATION.dho.wpdn",
                'dbname' => "HIDDENINFORMATION",
                'user' => "HIDDENINFORMATION",
                'password' => "HIDDENINFORMATION",
                'type' => "mysql",
                'flags' => DBO_DEFAULT,
                'load' => 1    //  < This means read ONLY
        );
}
```

-   Not all app servers are used full time by the caching layer, Fastly (Varnish). You can see that in [Fastly admin panel](https://app.fastly.com/), in the "Hosts" within "Configure" for the appropriate service. Current configuration is that two `app*` VMs have the load in equal portions (200), the 3rd VM is exposed as a backup load (190, see B, in attached image). The 3rd is ready if the two first ones can't serve all requests.
-   The cronjobs are run from a 4th app server that is not exposed at all. In the *app server VM listing* below, it's currently "app5".

![fastly-docs-service-hosts-screenshot.png](/WPD/assets/public/f/fb/fastly-docs-service-hosts-screenshot.png)

-   '*app server VM listing*. To know which VMs are `app*` servers, run the following.

``` html
renoirb@deployment:~$ nova list | grep app
| ... | app3  | ACTIVE | None       | Running     | vmnet=10.0.0.32, 208.113.157.171 |
| ... | app4  | ACTIVE | None       | Running     | vmnet=10.0.0.18, 208.113.157.173 |
| ... | app5  | ACTIVE | None       | Running     | vmnet=10.0.0.2, 208.113.157.166  |
| ... | app6  | ACTIVE | None       | Running     | vmnet=10.0.0.14, 208.113.157.162 |
```

## <span>Steps</span>

### <span>In summary</span>

1.  Make sure the "job runner" will not run during the whole process (e.g. comment all applicable crontab)
2.  Run SMW rebuild command
3.  Truncate job table
4.  Un comment the "job runner"

### <span>In detail</span>

-   Find the cron entries mentioning 'runJob.php' and comment them. This can be found by searching (`grep -rli 'runJob' /srv/salt`) in the salt state files. The job are assigned to the "`www-data`" user on the strongest app server (e.g. app4).
-   Make sure no job is running. The following shows it is fine.

``` html
root@deployment:~# salt 'app*' cmd.run 'ps aux | grep runJob'
app1:
    root     32739  0.0  0.0   9220  1188 ?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root     32741  0.0  0.0   6176   672 ?        S    00:14   0:00 grep unJob
app6:
    root     10650  0.0  0.0   9220  1188 ?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root     10652  0.0  0.0   6180   704 ?        S    00:14   0:00 grep unJob
app5:
    www-data 23979  0.0  0.0   4112   580 ?        Ss   14:44   0:00 /bin/sh -c /srv/webplatform/wiki/mediawiki-runJobs.sh #1st run
    www-data 23980  0.0  0.0   9228  1332 ?        S    14:44   0:00 /bin/bash -l /srv/webplatform/wiki/mediawiki-runJobs.sh
    www-data 23983  0.0  0.0   3876   412 ?        Ss   14:44   0:00 /usr/bin/timeout 3100 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    www-data 23984 71.7  0.6 203932 50700 ?        R    14:44  24:59 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    www-data 24347  0.0  0.0   4112   584 ?        Ss   15:16   0:00 /bin/sh -c /srv/webplatform/wiki/mediawiki-runJobs.sh #2nd run
    www-data 24348  0.0  0.0   9228  1328 ?        S    15:16   0:00 /bin/bash -l /srv/webplatform/wiki/mediawiki-runJobs.sh
    www-data 24351  0.0  0.0   3876   412 ?        Ss   15:16   0:00 /usr/bin/timeout 3100 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    www-data 24352 69.2  0.5 202424 49160 ?        S    15:16   1:59 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    root     24395  0.0  0.0   3876   408 pts/1    S+   15:18   0:00 /usr/bin/timeout 10800 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.ph
p
    root     24396 65.6  0.5 202472 49164 pts/1    R+   15:18   0:13 /usr/bin/php /srv/webplatform/wiki/current/maintenance/runJobs.php
    root     24403  0.0  0.0   9220  1188 ?        S    15:18   0:00 /bin/sh -c ps aux | grep unJob
    root     24405  0.0  0.0   6180   708 ?        S    15:18   0:00 grep unJob
app4:
    root      4183  0.0  0.0   9220  1188 ?        S    00:14   0:00 /bin/sh -c ps aux | grep unJob
    root      4185  0.0  0.0   6176   672 ?        S    00:14   0:00 grep unJob
```

-   Note that in this sample, we can see the use of the `/usr/bin/timeout` with various durations. The current salt configuration has the cronjob to run tasks for a maximum of 3100 seconds. The other job that has a duration of 10800 has been started manually to attempt emptying the queue.
-   Connect via SSH to the strongest app server with lowest weight in Fastly caching service. It is most likely the one that had crontabs with the `'runJob.php'` scheduled tasks.
-   Kill all related process on the server, and make sure they are not running anymore

``` html
root@app5:/srv/webplatform/wiki/test/extensions/SemanticMediaWiki/maintenance# kill -9 24395 24351 23983
root@app5:/srv/webplatform/wiki/test/extensions/SemanticMediaWiki/maintenance# ps aux | grep unJob
root     32427  0.0  0.0   7640   916 pts/3    S+   02:02   0:00 grep --color=auto unJob
```

-   Start a `screen` or `tmux` session and run the following from within it. That way, if your SSH connection dies, the script will continue to run.
-   Go to the appropriate folder where MediaWiki is installed. We have more than one installation, in this situation the appropriate place is in `/srv/webplatform/wiki/current/`. Always refer to the Salt states on the deployment server in `/srv/salt`
-   Run the Semantic Media Wiki refreshData script, it might take a while. Expect about 20 minutes of time to wait.

``` html
cd /srv/webplatform/wiki/wpwiki/mediawiki
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
29487 IDs refreshed.
```

-   If the job runner dies, you can use the ID it died on, and re-run the `SMW_refreshData.php` with the `-s` option.
-   When all is done, you can connect to the master database server and truncate the job table. Note that I made sure that the count is the same as I checked before running the `SMW_refreshData.php`.

``` html
mysql> use wpwiki;
mysql> SELECT COUNT(*) FROM job WHERE job_cmd LIKE '%SMW%';
+----------+
| COUNT(*) |
+----------+
|   318223 |
+----------+
mysql> truncate job;
Query OK, 0 rows affected (0.34 sec)
mysql> SELECT COUNT(*) FROM job WHERE job_cmd LIKE '%SMW%';
+----------+
| COUNT(*) |
+----------+
|        0 |
+----------+
1 row in set (0.00 sec)
```

-   All should be fine now!
-   Re-enable the jobRun in the appropriate cron jobs.

## <span>Reference</span>

-   [Repairing Semantic Media Wiki data](http://semantic-mediawiki.org/wiki/Help:Repairing_SMW's_data)
