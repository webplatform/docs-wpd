---
title: Site status problem notification messages
uri: 'WPD:Infrastructure/proposals/Site status problem notification messages'

---
## Description

In case of an site problem, some boilerplate error messages to start from. Generally we publish them to [status.webplatform.org](http://status.webplatform.org) and broadcast them to Twitter [@WebPlatform](https://twitter.com/WebPlatform) and other Social media accounts.

### TODO

-   When we need to block writes for backup/maintenance purposes
-   When a problem is caused by code being deployed [Example: this status text](http://status.twitter.com/post/63765159379/issue-viewing-timelines)
-   When we need to shut down
-   What to put as general note after a problem notification message
-   Maintenance window warning
-   Error pages text, add link to advise looking at **status.webplatform.org** site on [404 Error page](http://www.webplatform.org/errors/404.html), [503 Error page](http://www.webplatform.org/errors/503.html), and also (missing) **500 Error page**

### Inspiration and similar micro sites

-   [HP Cloud status](https://community.hpcloud.com/status)
-   [Twitter status](http://status.twitter.com)
-   [Facebook live status](https://developers.facebook.com/live_status/)

## Messages per problem type

### Generic

**Title:**: WebPlatform Site Issue

Some users may be experiencing an issue with our service. Our team are currently working on this issue.

### Currently working on (...)

We are currently working to repair a problem with (...) and in consequence affecting (...).

Some small down time might happen, but it is under control. We are sorry for the inconvenience.

### There has been issues (...)

(In case the issue is still unknown)

For the last two hours, there has been issues visiting or editing pages. We are investigating the situation and will keep you updated.

### Database server problem

The database server is currently not answering requests properly. Some pages are still available due to caching. We are investigating the situation and will keep you updated.

* * * * *

## Notifying problem resolution

1.  Prepend 'FIXED: ' to the status message title
2.  Add first line of status message **Update: This issue has been resolved as of 24:00 EST.**
3.  Put a **Original announcement** title before the original announcement message
4.  Describe what was the problem (optional)
5.  Add comment from first line status message "Update: ..." as comment on all social media sites that had the status report
