---
title: Site status problem notification messages
uri: 'WPD:Infrastructure/proposals/Site status problem notification messages'

---
## <span>Description</span>

In case of an site problem, some boilerplate error messages to start from. Generally we publish them to [status.webplatform.org](http://status.webplatform.org) and broadcast them to Twitter [@WebPlatform](https://twitter.com/WebPlatform) and other Social media accounts.

### <span>TODO</span>

-   When we need to block writes for backup/maintenance purposes
-   When a problem is caused by code being deployed [Example: this status text](http://status.twitter.com/post/63765159379/issue-viewing-timelines)
-   When we need to shut down
-   What to put as general note after a problem notification message
-   Maintenance window warning
-   Error pages text, add link to advise looking at **status.webplatform.org** site on [404 Error page](http://www.webplatform.org/errors/404.html), [503 Error page](http://www.webplatform.org/errors/503.html), and also (missing) **500 Error page**

### <span>Inspiration and similar micro sites</span>

-   [HP Cloud status](https://community.hpcloud.com/status)
-   [Twitter status](http://status.twitter.com)
-   [Facebook live status](https://developers.facebook.com/live_status/)

## <span>Messages per problem type</span>

### <span>Generic</span>

**Title:**: WebPlatform Site Issue

Some users may be experiencing an issue with our service. Our team are currently working on this issue.

### <span>Currently working on (...)</span>

We are currently working to repair a problem with (...) and in consequence affecting (...).

Some small down time might happen, but it is under control. We are sorry for the inconvenience.

### <span>There has been issues (...)</span>

(In case the issue is still unknown)

For the last two hours, there has been issues visiting or editing pages. We are investigating the situation and will keep you updated.

### <span>Database server problem</span>

The database server is currently not answering requests properly. Some pages are still available due to caching. We are investigating the situation and will keep you updated.

* * * * *

## <span>Notifying problem resolution</span>

1.  Prepend 'FIXED: ' to the status message title
2.  Add first line of status message **Update: This issue has been resolved as of 24:00 EST.**
3.  Put a **Original announcement** title before the original announcement message
4.  Describe what was the problem (optional)
5.  Add comment from first line status message "Update: ..." as comment on all social media sites that had the status report
