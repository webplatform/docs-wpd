= Site status problem notification messages =

== Description ==
In case of an site problem, some boilerplate error messages to start from. Generally we publish them to [http://status.webplatform.org status.webplatform.org] and broadcast them to Twitter [https://twitter.com/WebPlatform @WebPlatform] and other Social media accounts.

=== TODO ===
* When we need to block writes for backup/maintenance purposes
* When a problem is caused by code being deployed [http://status.twitter.com/post/63765159379/issue-viewing-timelines Example: this status text]
* When we need to shut down
* Error pages text, add link to advise looking at '''status.webplatform.org''' site on [http://www.webplatform.org/errors/404.html 404 Error page], [http://www.webplatform.org/errors/503.html 503 Error page], and also (missing) '''500 Error page'''

== Messages per problem type ==

=== Generic ===
'''Title:''': WebPlatform Site Issue

Some users may be experiencing an issue with our service. Our team are currently working on this issue.

=== Currently working on (...) ===

We are currently working to repair a problem with (...)  and in consequence affecting (...).

Some small down time might happen, but it is under control. We are sorry for the inconvenience.

=== There has been issues (...) ===
(In case the issue is still unknown)

For the last two hours, there has been issues visiting or editing pages. We are investigating the situation and will keep you updated.

=== Database server problem ===

The database server is currently not answering requests properly. Some pages are still available due to caching. We are investigating the situation and will keep you updated.

----

== Notifying problem resolution ==

# Prepend 'FIXED: ' to the status message title
# Add first line of status message '''Update: This issue has been resolved as of 24:00 EST.'''
# Put a '''Original announcement''' title before the original announcement message
# Describe what was the problem (optional)