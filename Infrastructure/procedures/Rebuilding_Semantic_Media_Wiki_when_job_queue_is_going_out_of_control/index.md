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


== Steps ==
=== In summary ===
# Make sure the "job runner" will not run during the whole process (e.g. comment all applicable crontab)
# Run SMW rebuild command
# Truncate job table
# Un comment the "job runner"


IMPORTANT: If the database setup has one master and multiple slav, make sure you do them on the master only, the slaves should follow. Doing the opposite might break the consistency of the database cluster.